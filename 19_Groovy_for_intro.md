# Groovy Basics for Jenkins Pipelines

## Contents
- [Intro](#intro)
- [Learning Objectives](#learning-objectives)
- [Lesson Outline](#lesson-outline)
  - [1. Introduction to Groovy](#1-introduction-to-groovy)
  - [2. Basic Groovy Syntax](#2-basic-groovy-syntax)
  - [3. Writing a Basic Jenkinsfile](#3-writing-a-basic-jenkinsfile)
  - [4. Key Jenkinsfile Components](#4-key-jenkinsfile-components)
  - [5. Hands-On Exercise](#5-hands-on-exercise)
  - [6. Homework](#6-homework)
- [Key Takeaways](#key-takeaways)

---

## Intro
This lesson introduces Groovy, the scripting language used in Jenkins Pipelines. Students will learn essential Groovy concepts and apply them to writing Jenkinsfiles, preparing them to automate build and deployment pipelines effectively.

---

## Learning Objectives
1. Understand what Groovy is and why it’s used in Jenkins Pipelines.
2. Learn basic Groovy syntax and concepts.
3. Write a simple Jenkinsfile using Groovy.
4. Understand the relationship between Groovy and Jenkins Pipeline DSL.

---

## Lesson Outline

### 1. Introduction to Groovy
- **What is Groovy?**
  - A dynamic, object-oriented programming language for the Java platform.
  - Simple to learn and integrates seamlessly with Java.
  - Jenkins Pipeline DSL is based on Groovy.

- **Why Groovy in Jenkins?**
  - Groovy is lightweight and expressive.
  - Allows you to write declarative or scripted pipelines in Jenkins.
  - Easy to embed Groovy code in Jenkinsfiles for custom logic.

---

### 2. Basic Groovy Syntax

###	Variables
groovy

```
def name = "Jenkins"
int number = 10
println("Hello, $name!")  // String interpolation
```

###	Data Types

```
def stringVar = "This is a string"
def intVar = 42
def listVar = [1, 2, 3, 4]
def mapVar = [key1: 'value1', key2: 'value2']
```
### Control Structures
	If-Else
```
if (number > 5) {
    println("Number is greater than 5")
} else {
    println("Number is 5 or less")
}
```
### Loops

```
// For Loop
for (i in 1..5) {
    println("Iteration: $i")
}
```
### While Loop

```
int count = 0
while (count < 3) {
    println("Count: $count")
    count++
}
```
### Functions

```
def greet(name) {
    return "Hello, $name!"
}

println(greet("Student"))
```

### Data Types

```
def stringVar = "This is a string"
def intVar = 42
def listVar = [1, 2, 3, 4]
def mapVar = [key1: 'value1', key2: 'value2']
```

### Writing a Basic Jenkinsfile

Declarative Pipeline Syntax

```
pipeline {
    agent any
    stages {
        stage('Hello World') {
            steps {
                echo 'Hello, World!'
            }
        }
    }
}

```

### Scripted Pipeline Syntax

```
node {
    stage('Hello World') {
        echo 'Hello, World!'
    }
}

```

### Key Jenkinsfile Components

1. Pipeline Block
    Defines the pipeline structure.
2. Agent
    Specifies where the pipeline should run (any or a specific node).
3. Stages
    Logical segments of the pipeline process.
4. Steps
    Actions to execute in each stage.

### Hands-On Exercise

Create a new pipeline project in Jenkins.

Write a simple Jenkinsfile:

Example code : git-practice.git repository



### Homework
- Write a Jenkinsfile that:

- Clones a Git repository.
- Prints the repository’s contents.
- Archives the project files.
- Explore basic Groovy concepts:

- Create a list and iterate over it.
- Define a function and call it from a script.


## Key Takeaways

- Groovy is the foundation for Jenkins Pipeline scripts.
- Understand how to use basic Groovy syntax like variables, loops, and functions.
- Learn the structure of a Jenkinsfile and the role of stages, steps, and agents.
