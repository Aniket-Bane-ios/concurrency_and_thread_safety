import Foundation


func performTaskWithoutTimeSlicing() {
    let tasks: [() -> Void] = [
        { for i in 1...5 { print("Task 1: \(i)") } },
        { for i in 1...5 { print("Task 2: \(i)") } },
        { for i in 1...5 { print("Task 3: \(i)") } }
    ]
    
    for task in tasks {
        task() // Runs each task fully before moving to the next
    }
    
    print("All tasks completed")
}

performTaskWithoutTimeSlicing()




func performTaskWithTimeSlicing() async {
    await withTaskGroup(of: Void.self) { group in
        for i in 1...3 {
            group.addTask {
                for j in 1...5 {
                    print("Task \(i): \(j)")
                    await Task.yield() // Allow other tasks to execute
                }
            }
        }
    }
    print("All tasks completed")
}

Task {
    await performTaskWithTimeSlicing()
}
