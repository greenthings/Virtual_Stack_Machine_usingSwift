# Virtual_Stack_Machine_usingSwift
Virtual Machine

```swift
class VirtualMachine{
  var programCount: Int = 0
  var stackPointer: Int = 0
  var stack: [Int] = []


  func function(_ program: [String]) {  
  
  //Run only when the length of the program is less than the program counter, i.e. exit the while statement when the program ends

  while programCount < program.count{
    
      // Program counter values are used as parameters in the program array and stored in current instruction.  
      let currentInstruction = program[programCount]
      
      // Divide the way through the switch door according to the recent command.
      switch currentInstruction{
        // If you want to push something, type-cast the following string as an integer and put it in the stack. 
        // And raise the stack pointer and program counter for the next current instruction.
        case "PUSH":
          stack.append(Int(program[programCount + 1]) ?? 0)
          stackPointer += 1
          programCount += 1

          print("Push: \(stack)")
          
        // If you want to add, you should pop action that is making two constant such as right and left for adding.
        // and then add them.
        case "ADD":

          let right: Int = stack[stackPointer - 1]
          stackPointer -= 1
          // You should remove last one, because it is stack machine.
          stack.removeLast()
          let left: Int = stack[stackPointer - 1]
          stackPointer -= 1
          stack.removeLast()

          print("POP: left: \(left),right: \(right)")
  
          stack.append(left + right)
          stackPointer += 1

          print("Add: \(stack)")
        
        case "MINUS":

          let right: Int = stack[stackPointer - 1]
          stackPointer -= 1
          stack.removeLast()
          let left: Int = stack[stackPointer - 1]
          stackPointer -= 1
          stack.removeLast()
          print("POP: left: \(left),right: \(right)")
          
          stack.append(abs(left - right))
          stackPointer += 1

          print("Minus: \(stack)")

        case "MULTIPLY":

           let right: Int = stack[stackPointer - 1]
          stackPointer -= 1
          stack.removeLast()
          let left: Int = stack[stackPointer - 1]
          stackPointer -= 1
          stack.removeLast()
          print("POP: left: \(left),right: \(right)")
          
          stack.append(left * right)
          stackPointer += 1

          print("Multiply: \(stack)")

        case "Divide":

          let right: Int = stack[stackPointer - 1]
          stackPointer -= 1
          stack.removeLast()
          let left: Int = stack[stackPointer - 1]
          stackPointer -= 1
          stack.removeLast()
          print("POP: left: \(left),right: \(right)")
          
          stack.append(left / right)
          stackPointer += 1

          print("Divide: \(stack)")  

        default: 
          print("Nothing")  
      }
      // This is for next instruction.
      programCount += 1
   }       
   print(stack)
}
}
```

# How to use it 
```swift

let virtualMachine = VirtualMachine()

let program = [
  "PUSH", "1",
  "PUSH", "7",
  "ADD",
  "PUSH", "2",
  "MINUS",
  "PUSH", "3",
  "MULTIPLY",
  "PUSH","2",
  "Divide"
]

virtualMachine.function(program)
```
