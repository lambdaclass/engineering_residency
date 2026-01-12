# Elixir Project: Forth Interpreter

[Forth](https://en.wikipedia.org/wiki/Forth_%28programming_language%29) is a stack-based programming language. 
Implement a very basic evaluator for a small subset of Forth.

In Forth, all syntactic elements, including variables, operators, and control flow, are defined as words.
A stack is used to pass parameters between words, leading to a Reverse Polish notation style.

Example code:
```forth
\ ------------------------------ Basic Arithmetic ------------------------------

\ Arithmetic (in fact most words requiring data) works by manipulating data on
\ the stack.
5 4 +    \ ok

\ `.` pops the top result from the stack:
.    \ 9 ok

\ More examples of arithmetic:
6 7 * .        \ 42 ok
1360 23 - .    \ 1337 ok
12 12 / .      \ 1 ok
13 2 mod .     \ 1 ok
```
- You can check more examples [here](https://learnxinyminutes.com/forth/). Note that these examples are for the full language. 

## Requirements:

Remember to follow the [general guidelines](readme.md#learning-projects-guidelines) for projects!

#### 1: Core language
The evaluator has to support the following words:
- `+`, `-`, `*`, `/` (integer arithmetic)
- `DUP`, `DROP`, `SWAP`, `OVER` (stack manipulation)

The evaluator also has to support defining new words using the customary syntax: `: word-name definition ;`.

To keep things simple, the only data type needed to support is signed integers of at least 16 bits size.

#### 2: User interface

The evaluator must also be available via a web interface served by Phoenix Liveview.

The user interface features must include:
- uploading a forth program
- requesting an evaluation
- showing the results
- a history of evaluated programs

Programs and executions must be persisted in PostgreSQL. 

## Tests

Aside from the functional requirements listed above, the following tests must be included in your project and pass:

```elixir
defmodule ForthTest do
  use ExUnit.Case
  doctest Forth

  # Helper function to evaluate Forth code and return the stack
  defp eval(code), do: Forth.eval(code, [])
  defp eval(code, initial_stack), do: Forth.eval(code, initial_stack)

  describe "basic number parsing" do
    test "parses single positive integer" do
      assert eval("5") == {:ok, [5]}
    end

    test "parses single negative integer" do
      assert eval("-5") == {:ok, [-5]}
    end

    test "parses multiple numbers" do
      assert eval("1 2 3") == {:ok, [1, 2, 3]}
    end

    test "parses zero" do
      assert eval("0") == {:ok, [0]}
    end

    test "handles large numbers" do
      assert eval("12345 67890") == {:ok, [12345, 67890]}
    end
  end

  describe "arithmetic operations" do
    test "+ adds two numbers" do
      assert eval("1 2 +") == {:ok, [3]}
    end

    test "+ adds multiple numbers" do
      assert eval("1 2 + 3 +") == {:ok, [6]}
    end

    test "- subtracts two numbers" do
      assert eval("5 3 -") == {:ok, [2]}
    end

    test "- with negative result" do
      assert eval("3 5 -") == {:ok, [-2]}
    end

    test "* multiplies two numbers" do
      assert eval("4 5 *") == {:ok, [20]}
    end

    test "* with negative numbers" do
      assert eval("-3 4 *") == {:ok, [-12]}
    end

    test "/ divides two numbers" do
      assert eval("20 4 /") == {:ok, [5]}
    end

    test "/ performs integer division" do
      assert eval("7 2 /") == {:ok, [3]}
    end

    test "/ with negative numbers" do
      assert eval("-10 2 /") == {:ok, [-5]}
    end

    test "/ by zero returns error" do
      assert eval("1 0 /") == {:error, "division by zero"}
    end

    test "complex arithmetic expression" do
      assert eval("1 2 + 3 * 4 -") == {:ok, [5]}
    end
  end

  describe "stack operations - dup" do
    test "dup duplicates top value" do
      assert eval("1 dup") == {:ok, [1, 1]}
    end

    test "dup with multiple values" do
      assert eval("1 2 dup") == {:ok, [1, 2, 2]}
    end

    test "dup on empty stack returns error" do
      assert eval("dup") == {:error, "stack underflow"}
    end
  end

  describe "stack operations - drop" do
    test "drop removes top value" do
      assert eval("1 2 drop") == {:ok, [1]}
    end

    test "drop leaves empty stack" do
      assert eval("1 drop") == {:ok, []}
    end

    test "drop on empty stack returns error" do
      assert eval("drop") == {:error, "stack underflow"}
    end
  end

  describe "stack operations - swap" do
    test "swap exchanges top two values" do
      assert eval("1 2 swap") == {:ok, [2, 1]}
    end

    test "swap with more values on stack" do
      assert eval("1 2 3 swap") == {:ok, [1, 3, 2]}
    end

    test "swap with one value returns error" do
      assert eval("1 swap") == {:error, "stack underflow"}
    end

    test "swap on empty stack returns error" do
      assert eval("swap") == {:error, "stack underflow"}
    end
  end

  describe "stack operations - over" do
    test "over copies second value to top" do
      assert eval("1 2 over") == {:ok, [1, 2, 1]}
    end

    test "over with more values on stack" do
      assert eval("1 2 3 over") == {:ok, [1, 2, 3, 2]}
    end

    test "over with one value returns error" do
      assert eval("1 over") == {:error, "stack underflow"}
    end

    test "over on empty stack returns error" do
      assert eval("over") == {:error, "stack underflow"}
    end
  end

  describe "stack operations - rot" do
    test "rot rotates top three values" do
      assert eval("1 2 3 rot") == {:ok, [2, 3, 1]}
    end

    test "rot with more values on stack" do
      assert eval("1 2 3 4 rot") == {:ok, [1, 3, 4, 2]}
    end

    test "rot with two values returns error" do
      assert eval("1 2 rot") == {:error, "stack underflow"}
    end

    test "rot on empty stack returns error" do
      assert eval("rot") == {:error, "stack underflow"}
    end
  end

  describe "combined stack operations" do
    test "dup swap combination" do
      assert eval("1 2 dup swap") == {:ok, [1, 2, 2]}
    end

    test "over swap drop combination" do
      assert eval("1 2 over swap drop") == {:ok, [1, 1]}
    end

    test "complex stack manipulation" do
      assert eval("1 2 3 swap over") == {:ok, [1, 3, 2, 3]}
    end
  end

  describe "comparison operations" do
    test "= returns -1 for equal values" do
      assert eval("5 5 =") == {:ok, [-1]}
    end

    test "= returns 0 for different values" do
      assert eval("5 3 =") == {:ok, [0]}
    end

    test "> returns -1 when first is greater" do
      assert eval("5 3 >") == {:ok, [-1]}
    end

    test "> returns 0 when first is not greater" do
      assert eval("3 5 >") == {:ok, [0]}
    end

    test "> returns 0 when equal" do
      assert eval("5 5 >") == {:ok, [0]}
    end

    test "< returns -1 when first is less" do
      assert eval("3 5 <") == {:ok, [-1]}
    end

    test "< returns 0 when first is not less" do
      assert eval("5 3 <") == {:ok, [0]}
    end

    test "< returns 0 when equal" do
      assert eval("5 5 <") == {:ok, [0]}
    end

    test "comparison on empty stack returns error" do
      assert eval("=") == {:error, "stack underflow"}
    end
  end

  describe "logical operations" do
    test "and returns -1 when both are true" do
      assert eval("-1 -1 and") == {:ok, [-1]}
    end

    test "and returns 0 when first is false" do
      assert eval("0 -1 and") == {:ok, [0]}
    end

    test "and returns 0 when second is false" do
      assert eval("-1 0 and") == {:ok, [0]}
    end

    test "and returns 0 when both are false" do
      assert eval("0 0 and") == {:ok, [0]}
    end

    test "or returns -1 when both are true" do
      assert eval("-1 -1 or") == {:ok, [-1]}
    end

    test "or returns -1 when first is true" do
      assert eval("-1 0 or") == {:ok, [-1]}
    end

    test "or returns -1 when second is true" do
      assert eval("0 -1 or") == {:ok, [-1]}
    end

    test "or returns 0 when both are false" do
      assert eval("0 0 or") == {:ok, [0]}
    end

    test "not inverts false to true" do
      assert eval("0 not") == {:ok, [-1]}
    end

    test "not inverts true to false" do
      assert eval("-1 not") == {:ok, [0]}
    end

    test "not inverts any non-zero to false" do
      assert eval("5 not") == {:ok, [0]}
    end

    test "invert performs bitwise NOT" do
      assert eval("0 invert") == {:ok, [-1]}
    end

    test "invert with -1" do
      assert eval("-1 invert") == {:ok, [0]}
    end
  end

  describe "case insensitivity" do
    test "operations are case insensitive" do
      assert eval("1 2 DUP") == {:ok, [1, 2, 2]}
      assert eval("1 2 Dup") == {:ok, [1, 2, 2]}
      assert eval("1 2 DROP") == {:ok, [1]}
      assert eval("1 2 SWAP") == {:ok, [2, 1]}
    end

    test "mixed case arithmetic" do
      assert eval("1 2 +") == eval("1 2 PLUS") || {:ok, [3]}
    end
  end

  describe "user-defined words" do
    test "can define and use custom word" do
      assert eval(": double dup + ; 5 double") == {:ok, [10]}
    end

    test "can define word using other operations" do
      assert eval(": square dup * ; 4 square") == {:ok, [16]}
    end

    test "can define word using other custom words" do
      assert eval(": double dup + ; : quadruple double double ; 3 quadruple") == {:ok, [12]}
    end

    test "cannot redefine numbers" do
      assert eval(": 1 2 ;") == {:error, "invalid word definition"}
    end

    test "cannot define empty word" do
      assert eval(": ;") == {:error, "invalid word definition"}
    end

    test "definition without terminator returns error" do
      assert eval(": double dup +") == {:error, "unterminated definition"}
    end
  end

  describe "additional stack operations" do
    test "nip removes second value" do
      assert eval("1 2 nip") == {:ok, [2]}
    end

    test "tuck copies top below second" do
      assert eval("1 2 tuck") == {:ok, [2, 1, 2]}
    end

    test "2dup duplicates top two values" do
      assert eval("1 2 2dup") == {:ok, [1, 2, 1, 2]}
    end

    test "2drop removes top two values" do
      assert eval("1 2 3 2drop") == {:ok, [1]}
    end

    test "2swap swaps top two pairs" do
      assert eval("1 2 3 4 2swap") == {:ok, [3, 4, 1, 2]}
    end

    test "2over copies second pair to top" do
      assert eval("1 2 3 4 2over") == {:ok, [1, 2, 3, 4, 1, 2]}
    end
  end

  describe "edge cases and errors" do
    test "empty input returns empty stack" do
      assert eval("") == {:ok, []}
    end

    test "whitespace only returns empty stack" do
      assert eval("   ") == {:ok, []}
    end

    test "invalid operation returns error" do
      assert eval("invalid") == {:error, "unknown word: invalid"}
    end

    test "arithmetic on insufficient values returns error" do
      assert eval("1 +") == {:error, "stack underflow"}
    end

    test "arithmetic with no values returns error" do
      assert eval("+") == {:error, "stack underflow"}
    end

    test "mixed valid and invalid operations" do
      assert eval("1 2 + invalid") == {:error, "unknown word: invalid"}
    end
  end

  describe "real world examples" do
    test "calculating area: (width * height)" do
      assert eval("5 3 *") == {:ok, [15]}
    end

    test "calculating average: (a + b) / 2" do
      assert eval("10 20 + 2 /") == {:ok, [15]}
    end

    test "distance formula component: (x2 - x1)^2" do
      assert eval(": square dup * ; 5 3 - square") == {:ok, [4]}
    end

    test "celsius to fahrenheit: C * 9 / 5 + 32" do
      assert eval("100 9 * 5 / 32 +") == {:ok, [212]}
    end

    test "swap values using stack operations" do
      assert eval("1 2 swap") == {:ok, [2, 1]}
    end
  end

  describe "initial stack state" do
    test "evaluates with non-empty initial stack" do
      assert eval("1 +", [5]) == {:ok, [6]}
    end

    test "operations work on initial stack values" do
      assert eval("dup +", [10]) == {:ok, [20]}
    end

    test "can clear initial stack" do
      assert eval("drop drop", [1, 2]) == {:ok, []}
    end
  end
end
```