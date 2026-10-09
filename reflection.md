# Reflection: Integer Overflow Lab

*Draft: Review and personalize this reflection so it accurately describes your own experience before submitting it.*

For this project, I used AI-assisted development to build an interactive visualization of integer overflow. I chose this topic because seeing a number suddenly become zero or negative can be confusing when only looking at code. The application connects the mathematical answer to the actual bit pattern that a fixed-width value can store.

My workflow began by defining the learning goal and choosing the controls: bit width, signed or unsigned interpretation, two operands, and an arithmetic operation. I used AI to help generate the HTML, CSS, JavaScript, and documentation. The next part of the workflow was checking boundary examples and browser interactions, including unsigned 255 + 1, signed 127 + 1 in the model, negative results, multiplication, and invalid inputs. I would also review the generated code and explain the remainder calculation myself before submitting the project.

The most useful part of the visualization is comparing the full mathematical result with the stored value. For an unsigned 8-bit value, 255 + 1 gives 256 mathematically, but only eight bits are retained, leaving zero. Switching to signed mode also shows that the same bit pattern can mean a different number. For example, 10000000 represents 128 as unsigned and -128 as signed two's complement.

This project helped clarify the difference between a bit pattern and its interpretation. It also highlighted an important limitation: the application's signed wraparound is a teaching model, while signed overflow in C and C++ is undefined behavior. The prediction challenges encourage learners to work out the answer before checking it. AI made it easier to produce a usable first version, but understanding and verifying the model remains an essential part of the development process.
