# Virtual_Stack_Machine_usingSwift
Virtual Machine

```swift
class VirtualMachine{
  var programCount: Int = 0
  var stackPointer: Int = 0
  var stack: [Int] = []


  func function(_ program: [String]) {  

  while programCount < program.count{

      let currentInstruction = program[programCount]

      switch currentInstruction{
        case "PUSH":
          stack.append(Int(program[programCount + 1]) ?? 0)
          stackPointer += 1
          programCount += 1

          print("Push: \(stack)")

        case "ADD":

          let right: Int = stack[stackPointer - 1]
          stackPointer -= 1
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
