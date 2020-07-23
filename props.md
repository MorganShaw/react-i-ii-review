### Remember

Answer these on your own, then compare answers as a group

1.  What are props?
    Data - about an object... That can be passed from parent to child component.  Can pass down function, string, array, object. The prop itself is an object, as a key value pair (remember how child element is shown in render method of parent component - List key= and value=. But

2.  How do you pass props from a parent to a child?


3.  How do you access props from a class-based child component?
  Pass props parameter in constructor and super functions. 

4.  How do you access props from a functional component?
  Pass props as a parameter in the function.

5.  How do you bind a function to a parent component so that it can be passed to a child?
this.functionName = this.functionName.bind(this) inside the constructor function. So it has the explicit context of this.


### Understand

Discuss this question in pairs if you have a 4-person group

6.  What's happening in this component?

```jsx
import React, { Component } from "react";

class Queue extends Component {
  constructor(props) {
    super(props);

    this.state = {
      questions: []
    };

    this.askQuestion = this.askQuestion.bind(this);
    this.answerQuestion = this.answerQuestion.bind(this);
  }
  askQuestion(newQuestion) {
    const questions = [...this.state.questions, newQuestion];
    this.setState({ questions });
  }
  answerQuestion(index) {
    const questions = [...this.state.questions];
    questions.splice(index, 1);
    this.setState({ questions });
  }
  render() {
    <div className="queue-container">
      <h1>The Queue</h1>
      <h3>{this.state.questions.length}</h3>
      <h3>questions need answers</h3>
      <Student askQuestion={this.askQuestion} />
      <Mentor answerQuestion={this.answerQuestion} />
    </div>;
  }
}
```
//On student, you'd see askQuestion = {this.props.????}
### Apply

Try these on your own, but work together if you start to get stuck.

7.  Using the `Queue` component above, create a `Student` component that can add a question as a string and a `Mentor` component that can remove a question from the array.
Student would be class, and mentor would be functional.

can be functional component. Ask question is written in this component (parent component queue).

class Student extends Component {
  constructor 
  

### Analyze, Evaluate, Create

Discuss these questions as a group

8.  In the Queue component above, why are we holding state in the Queue component instead of Mentor or Student?
???
Because state needs to be available in mentor and student (the children). If it was on one or the other, you can't pass data back up to parent and then down to other child. Data passed down to student (child), and event bubbling back up to Queue (parent).
