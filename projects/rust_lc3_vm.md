# Rust Project: LC3 VM

Read the following article: [Write your own virtual machine](https://justinmeiners.github.io/lc3-vm/).

The goal of this project is to implement the LC3 VM in Rust. 
The article shows how to do it in C, so it shouldn't be too hard. 
However, this project involves considerably more functionality than the previous ones.
The VM has has several opcodes and a memory model that must be respected. 

One of the common pitfalls is to implement too much before having proper integration tests. 
Another common pitfall is to test opcode functionality individually, but not how they work together in a real program.

As always, try to keep the code simple and do not overengineer the solution. 

Finally, your VM must be able to run the [roguelike](https://github.com/justinmeiners/lc3-rogue) from the terminal.

Remember to follow the [general guidelines](readme.md#learning-projects-guidelines) for projects!
