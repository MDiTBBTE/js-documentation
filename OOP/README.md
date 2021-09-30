In JS exist 4 paradigms of OOP which should everyone knows and don't avoid them in using

Four whales 
1) Abstraction
2) Inheritance
3) Encapsulation
4) Polymorphism

###### 1. What is ***abstraction*** ?

Just imagine that we have a website on which u see a lot of different buttons 
on different pages. What u think about this thing ? Sure, that u don't want to create 
new class for each of them. Now, we're steadily going to the ***abstraction*** by means of which we
can highlight main features and create only class

```javascript
class Button {
    constructor(text, color) {
        this.text = text;
        this.color = color;
        this.isPressed = false;
    }

    pressButton() {
        this.isPressed = !this.isPressed;
    }
}
```

For instance, I add to the btn text, color and ability to press on this btn.
These are our characteristics which are unchanged for every button.

###### 2. What is ***inheritance*** ?
As we know from the previous story, we have different buttons on pages, so we need to have all of them and
instead of creating a new button every time we can just inherit the main ```class Button```

```javascript
const socialButton = new Button('Twitter', 'blue');
```

###### 3. What is ***encapsulation*** ?

Let's try to imagine such situation that our customer go te the signup form 
and fill in login, password and many other fields. After this he just presses button Signup and wait for the result, after that go to the website.
Okay, I think u imagine this, it was easy. Bat what if our user dive in the implementation of the registration process and see sth like this

```javascript
class Button {
    constructor(text, color) {
        this.text = text;
        this.color = color;
        this.isPressed = false;
    }

    togglePress () {
        this.isPressed = !this.isPressed
    }

    pressButton() {
        this.togglePress()
    }
}

class SignUpButton extends Button {
    constructor(text, color, email, password) {
        super(text, color);
        isValid = false;
        this.email = email;
        this.password = password;
    }
    
    _validateFields() {
        const isEmailValid = this.email.includes('@')
        const isPasswordValid = this.password.length !== 0;

        isEmailValid && isPasswordValid ? 
            this.isValid = true :
            this.isValid = false;
    }
    
    createUser() {
        this._validateFields();
        
        this.isValid ? this.pressButton() : null;
    }
}

const signUpButton = new Button('SignUp', 'blue', 'email@gmail.com', 'password');

```

As u could understand, it's a bit tricky for him to figure out what is going on.
Because of this, we should to hide our internal logic. Actually he even doesn't need to know that is under the hood after
the pressing of signup button. We just show him what he should see, in our case it's an inscription Signup on the button.

###### 4. What is ***polymorphism*** ?

This part is a bit harder than previous, but I'm convinced that u understand after the explanation.
Let's look on the example. Imagine that we have such a function like ```getArea``` which should calculate the area of the shape.

```javascript
const getArea = (value) => 'make some calculation with value'
```

We have a lot of different shapes, but we pay attention on the square and circle. After we declared the classes, we can see a ```shapes``` variable which contains
like circles so square in array. Then u also see that we use forEach for checking all these shapes and calculate their area.

```javascript

class Square {
    constructor(sideSize) {
        this.sideSize = sideSize;
    }

    getArea () {
        return sideSize * sideSize;
    }
}

class Circle {
    constructor(sideSize) {
        this.sideSize = sideSize;
        this.PI = 3.14;
    }

    getArea () {
        return PI * sideSize * sideSize;
    }
}

const shapes = [new Circle(5), new Square(2), new Circle(3)]

shapes.forEach( shape => shape.getArea());
```
Actually, the polymorphism is a paradigm that provides a way to perform a single action in different forms. It provides an ability to call the same method on different JavaScript objects.
