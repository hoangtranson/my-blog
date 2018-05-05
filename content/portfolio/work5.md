+++
showonlyimage = false
draft = false
image = "img/portfolio/content5/js1.jpeg"
date = "2018-04-1T23:00:00+07:00"
title = "Clean Code Javascript"
weight = 2
+++

Software engineering principles, from Robert C. Martin's book Clean Code.
<!--more-->

### Table of content
- [Introduction](#introduction)
- [Summary and Integrate to PR](#summary)
- [Variables](#variables)
- [Functions](#functions)
- [Objects and Data Structures](#objectandDSA)
- [Classes](#classes)
- [SOLID](#solid)
- [Testing](#testing)
- [Concurrency](#concurrency)
- [Error Handling](#errorhandling)
- [Formatting](#formatting)
- [Comments](#comments)

#### Introduction <a name="introduction"></a>

This topic based on [Clean code javascript](https://github.com/ryanmcdermott/clean-code-javascript) from Ryanmc Dermott. Thanks to his great work. I created my check list for javascript from this great resource and this help me a lot in reducing bugs and optimize my code. That's why I wanna share this to persons who is working as Front-end engineering like me.

#### Summary and Integrate to PR <a name="summary"></a>

Here is check list that I created by myself.

```Markdown
Variables
- [ ] Use meaningful and pronounceable variable names
- [ ] Use the same vocabulary for the same type of variable
- [ ] Use searchable names
- [ ] Avoid Mental Mapping
- [ ] Don't add unneeded context
- [ ] Use default arguments instead of short circuiting or conditionals

Functions
- [ ] Function arguments (2 or fewer ideally)
- [ ] Functions should do one thing
- [ ] Function names should say what they do
- [ ] Remove duplicate code
- [ ] Set default objects with Object.assign
- [ ] Don't use flags as function parameters
- [ ] Favor functional programming over imperative programming
- [ ] Encapsulate conditionals
- [ ] Avoid negative conditionals
- [ ] Avoid conditionals
- [ ] Avoid type-checking
- [ ] Don't over-optimize
- [ ] Remove dead code

Objects and Data Structures
- [ ] Use getters and setters
- [ ] Make objects have private members

Classes
- [ ] Prefer ES2015/ES6 classes over ES5 plain functions
- [ ] Use method chaining
- [ ] Prefer composition over inheritance

SOLID
- [ ] Single Responsibility Principle (SRP)
- [ ] Open/Closed Principle (OCP)
- [ ] Liskov Substitution Principle (LSP)
- [ ] Interface Segregation Principle (ISP)
- [ ] Dependency Inversion Principle (DIP)

Testing
- [ ] Single concept per test

Concurrency
- [ ] Use Promises, not callbacks
- [ ] Async/Await are even cleaner than Promises

Error Handling
- [ ] Don't ignore caught errors
- [ ] Don't ignore rejected promises

Formatting
- [ ] Use consistent capitalization
- [ ] Function callers and callees should be close

Comments
- [ ] Only comment things that have business logic complexity.
- [ ] Don't leave commented out code in your codebase
- [ ] Don't have journal comments
- [ ] Avoid positional markers
```

![image 1][1]

![image 2][2]

So I use this as check list whenever I create pull request to important branchs.

#### Variables <a name="variables"></a>

1. Use meaningful and pronounceable variable names

    BAD CODE:
    ```Javascript
    const yyyymmdstr = moment().format('YYYY/MM/DD');
    ```

    GOOD CODE:
    ```Javascript
    const currentDate = moment().format('YYYY/MM/DD'); // change var name more meaning
    ```

2. Use the same vocabulary for the same type of variable

    BAD CODE:
    ```Javascript
    getUserInfo();
    getClientData();
    getCustomerRecord();
    ```

    GOOD CODE:
    ```Javascript
    getUser();
    ```
3. Use searchable names

    We will read more code than we will ever write. It's important that the code we do write is readable and searchable. By not naming variables that end up being meaningful for understanding our program, we hurt our readers. Make your names searchable. Tools like [buddy.js](https://github.com/danielstjules/buddy.js) and [ESLint](https://github.com/eslint) can help identify unnamed constants.

    BAD CODE:
    ```Javascript
    setTimeout(blastOff, 86400000);
    ```

    GOOD CODE:
    ```Javascript
    const MILLISECONDS_IN_A_DAY = 86400000; // create MILLISECONDS_IN_A_DAY for 86400000
    setTimeout(blastOff, MILLISECONDS_IN_A_DAY);
    ```

4. Avoid Mental Mapping
    Explicit is better than implicit.

    BAD CODE:
    ```Javascript
    const locations = ['Austin', 'New York', 'San Francisco'];
    locations.forEach((l) => {
        doStuff();
        doSomeOtherStuff();
        dispatch(l);
    });
    ```

    GOOD CODE:
    ```Javascript
    const locations = ['Austin', 'New York', 'San Francisco'];
    locations.forEach((location) => { // change l to location
        doStuff();
        doSomeOtherStuff();
        dispatch(location);
    });
    ```

5. Don't add unneeded context
    If your class/object name tells you something, don't repeat that in your variable name.

    BAD CODE:
    ```Javascript
    const Car = {
        carMake: 'Honda',
        carModel: 'Accord',
        carColor: 'Blue'
    };

    paintCar(car) {
        car.carColor = 'Red';
    }
    ```

    GOOD CODE:
    ```Javascript
    const Car = {
        make: 'Honda',
        model: 'Accord',
        color: 'Blue'
    };

    paintCar(car) {
        car.carColor = 'Red';
    }
    ```

6. Use default arguments instead of short circuiting or conditionals
    Default arguments are often cleaner than short circuiting. Be aware that if you use them, your function will only provide default values for undefined arguments. Other "falsy" values such as '', "", false, null, 0, and NaN, will not be replaced by a default value.

    BAD CODE:
    ```Javascript
    createMicrobrewery(name) {
        const breweryName = name || 'Hipster Brew Co.';
        ...
    }
    ```

    GOOD CODE:
    ```Javascript
    createMicrobrewery(name = 'Hipster Brew Co.') {
        ...
    }
    ```

#### Functions <a name="functions"></a>

1. Function arguments (2 or fewer ideally)

    Limiting the amount of function parameters is incredibly important because it makes testing your function easier. Having more than three leads to a combinatorial explosion where you have to test tons of different cases with each separate argument.

    One or two arguments is the ideal case, and three should be avoided if possible. Anything more than that should be consolidated. Usually, if you have more than two arguments then your function is trying to do too much. In cases where it's not, most of the time a higher-level object will suffice as an argument.

    Since JavaScript allows you to make objects on the fly, without a lot of class boilerplate, you can use an object if you are finding yourself needing a lot of arguments.

    To make it obvious what properties the function expects, you can use the ES2015/ES6 destructuring syntax. This has a few advantages:

    - When someone looks at the function signature, it's immediately clear what properties are being used.
    - Destructuring also clones the specified primitive values of the argument object passed into the function. This can help prevent side effects. Note: objects and arrays that are destructured from the argument object are NOT cloned.
    - Linters can warn you about unused properties, which would be impossible without destructuring.

    BAD CODE:
    ```Javascript
    createMenu(title, body, buttonText, cancellable) {
    }
    ```

    GOOD CODE:
    ```Javascript
    createMenu({ title, body, buttonText, cancellable }) {
    }

    createMenu({
        title: 'Foo',
        body: 'Bar',
        buttonText: 'Baz',
        cancellable: true
    });
    ```

2. Functions should do one thing

    This is by far the most important rule in software engineering. When functions do more than one thing, they are harder to compose, test, and reason about. When you can isolate a function to just one action, they can be refactored easily and your code will read much cleaner. If you take nothing else away from this guide other than this, you'll be ahead of many developers.

    BAD CODE:
    ```Javascript
    emailClients(clients) {
        clients.forEach((client) => {
            const clientRecord = database.lookup(client);
            if (clientRecord.isActive()) {
                email(client);
            }
        });
    }
    ```

    GOOD CODE:
    ```Javascript
    emailActiveClients(clients) {
        clients
            .filter(isActiveClient)
            .forEach(email);
        }

    isActiveClient(client) {
        const clientRecord = database.lookup(client);
        return clientRecord.isActive();
    }
    ```

3. Function names should say what they do

    It's hard to tell from the function name what is added

    BAD CODE:
    ```Javascript
    addToDate(date, month) {}
    const date = new Date();
    addToDate(date, 1);
    ```

    GOOD CODE:
    ```Javascript
    addMonthToDate(month, date) {}
    const date = new Date();
    addMonthToDate(1, date)
    ```

4. Remove duplicate code
    Do your absolute best to avoid duplicate code. Duplicate code is bad because it means that there's more than one place to alter something if you need to change some logic.

    Imagine if you run a restaurant and you keep track of your inventory: all your tomatoes, onions, garlic, spices, etc. If you have multiple lists that you keep this on, then all have to be updated when you serve a dish with tomatoes in them. If you only have one list, there's only one place to update!

    Oftentimes you have duplicate code because you have two or more slightly different things, that share a lot in common, but their differences force you to have two or more separate functions that do much of the same things. Removing duplicate code means creating an abstraction that can handle this set of different things with just one function/module/class.

    Getting the abstraction right is critical, that's why you should follow the SOLID principles laid out in the Classes section. Bad abstractions can be worse than duplicate code, so be careful! Having said this, if you can make a good abstraction,do it! Don't repeat yourself, otherwise you'll find yourself updating multiple places anytime you want to change one thing.

    BAD CODE:
    ```Javascript
    showDeveloperList(developers) {
        developers.forEach((developer) => {
            const expectedSalary = developer.calculateExpectedSalary();
            const experience = developer.getExperience();
            const githubLink = developer.getGithubLink();
            const data = {
            expectedSalary,
            experience,
            githubLink
            };

            render(data);
        });
    }

    showManagerList(managers) {
        managers.forEach((manager) => {
            const expectedSalary = manager.calculateExpectedSalary();
            const experience = manager.getExperience();
            const portfolio = manager.getMBAProjects();
            const data = {
            expectedSalary,
            experience,
            portfolio
            };

            render(data);
        });
    }
    ```

    GOOD CODE:
    ```Javascript
    showEmployeeList(employees) {
        employees.forEach((employee) => {
            const expectedSalary = employee.calculateExpectedSalary();
            const experience = employee.getExperience();

            const data = {
            expectedSalary,
            experience
            };

            switch (employee.type) {
            case 'manager':
                data.portfolio = employee.getMBAProjects();
                break;
            case 'developer':
                data.githubLink = employee.getGithubLink();
                break;
            }

            render(data);
        });
    }
    ```

5. Set default objects with Object.assign
    BAD CODE:
    ```Javascript
    const menuConfig = {
        title: null,
        body: 'Bar',
        buttonText: null,
        cancellable: true
    };

    createMenu(config) {
        config.title = config.title || 'Foo';
        config.body = config.body || 'Bar';
        config.buttonText = config.buttonText || 'Baz';
        config.cancellable = config.cancellable !== undefined ? config.cancellable : true;
    }

    createMenu(menuConfig);
    ```

    GOOD CODE:
    ```Javascript
    const menuConfig = {
        title: 'Order',
        buttonText: 'Send',
        cancellable: true
    };

    createMenu(config) {
        config = Object.assign({
            title: 'Foo',
            body: 'Bar',
            buttonText: 'Baz',
            cancellable: true
        }, config);
    }

    createMenu(menuConfig);
    ```
6. Don't use flags as function parameters

    Flags tell your user that this function does more than one thing. Functions should do one thing. Split out your functions if they are following different code paths based on a boolean.

    BAD CODE:
    ```Javascript
    createFile(name, temp) {
        if (temp) {
            fs.create(`./temp/${name}`);
        } else {
            fs.create(name);
        }
    }
    ```

    GOOD CODE:
    ```Javascript
    createFile(name) {
        fs.create(name);
    }

    createTempFile(name) {
        createFile(`./temp/${name}`);
    }
    ```

7. Favor functional programming over imperative programming

    JavaScript isn't a functional language in the way that Haskell is, but it has a functional flavor to it. Functional languages can be cleaner and easier to test. Favor this style of programming when you can.

    BAD CODE:
    ```Javascript
    const programmerOutput = [
        {
            name: 'Uncle Bobby',
            linesOfCode: 500
        }, {
            name: 'Suzie Q',
            linesOfCode: 1500
        }, {
            name: 'Jimmy Gosling',
            linesOfCode: 150
        }, {
            name: 'Gracie Hopper',
            linesOfCode: 1000
        }
    ];

    let totalOutput = 0;

    for (let i = 0; i < programmerOutput.length; i++) {
        totalOutput += programmerOutput[i].linesOfCode;
    }
    ```

    GOOD CODE:
    ```Javascript
    const programmerOutput = [
        {
            name: 'Uncle Bobby',
            linesOfCode: 500
        }, {
            name: 'Suzie Q',
            linesOfCode: 1500
        }, {
            name: 'Jimmy Gosling',
            linesOfCode: 150
        }, {
            name: 'Gracie Hopper',
            linesOfCode: 1000
        }
    ];

    const totalOutput = programmerOutput
    .map(output => output.linesOfCode)
    .reduce((totalLines, lines) => totalLines + lines);
    ```
8. Encapsulate conditionals
    BAD CODE:
    ```Javascript
    if (fsm.state === 'fetching' && isEmpty(listNode)) {}
    ```

    GOOD CODE:
    ```Javascript
    shouldShowSpinner(fsm, listNode) {
        return fsm.state === 'fetching' && isEmpty(listNode);
    }

    if (shouldShowSpinner(fsmInstance, listNodeInstance)) {}
    ```
9. Avoid negative conditionals
    BAD CODE:
    ```Javascript
    isDOMNodeNotPresent(node) {}
    if (!isDOMNodeNotPresent(node)) {}
    ```

    GOOD CODE:
    ```Javascript
    isDOMNodePresent(node) {}

    if (isDOMNodePresent(node)) {}
    ```
10. Avoid conditionals

    This seems like an impossible task. Upon first hearing this, most people say, "how am I supposed to do anything without an if statement?" The answer is that you can use polymorphism to achieve the same task in many cases. The second question is usually, "well that's great but why would I want to do that?" The answer is a previous clean code concept we learned: a function should only do one thing. When you have classes and functions that have if statements, you are telling your user that your function does more than one thing. Remember, just do one thing.

    BAD CODE:
    ```Javascript
    class Airplane {
        getCruisingAltitude() {
            switch (this.type) {
                case '777':
                    return this.getMaxAltitude() - this.getPassengerCount();
                case 'Air Force One':
                    return this.getMaxAltitude();
                case 'Cessna':
                    return this.getMaxAltitude() - this.getFuelExpenditure();
            }
        }
    }
    ```

    There are multiple issues with switch, from its procedural control flow to its non-standard-looking way it handles code blocks, the rest of JavaScript uses curly braces yet switch does not. Syntactically, it’s not one of JavaScript’s best, nor is its design. We’re forced to manually add break; statements within each case, which can lead to difficult debugging and nested errors further down the case should we forget! Douglas Crockford has written and spoken about it numerous times, his recommendations are to treat it with caution.

    We often use Object lookups for things in JavaScript, often for things we would never contemplate using switch for - so why not use an Object literal to replace switch? Objects are much more flexible, have better readability and maintainability and we don’t need to manually break; each “case”. They’re a lot friendlier on new JavaScript developers as well, as they’re standard Objects.

    As the number of “cases” increases, the performance of the object (hash table) gets better than the average cost of the switch (the order of the cases matter). The object approach is a hash table lookup, and the switch has to evaluate each case until it hits a match and a break.

    GOOD CODE:
    ```Javascript
    class Airplane {
        getCruisingAltitude (type) {
            const CruisingAltitude = {
                '777': () => {
                    return this.getMaxAltitude() - this.getPassengerCount();
                },
                'Air Force One': () => {
                    return this.getMaxAltitude();
                },
                'Cessna': () => {
                    return this.getMaxAltitude() - this.getFuelExpenditure();
                }
            };
            return CruisingAltitude[type]();
        }
    }
    ```
11. Avoid type-checking

    JavaScript is untyped, which means your functions can take any type of argument. Sometimes you are bitten by this freedom and it becomes tempting to do type-checking in your functions. There are many ways to avoid having to do this. The first thing to consider is consistent APIs.

    BAD CODE:
    ```Javascript
    travelToTexas(vehicle) {
        if (vehicle instanceof Bicycle) {
            vehicle.pedal(this.currentLocation, new Location('texas'));
        } else if (vehicle instanceof Car) {
            vehicle.drive(this.currentLocation, new Location('texas'));
        }
    }
    ```

    GOOD CODE:
    ```Javascript
    travelToTexas(vehicle) {
        vehicle.move(this.currentLocation, new Location('texas'));
    }
    ```

    If you are working with basic primitive values like strings and integers, and you can't use polymorphism but you still feel the need to type-check, you should consider using TypeScript. It is an excellent alternative to normal JavaScript, as it provides you with static typing on top of standard JavaScript syntax. The problem with manually type-checking normal JavaScript is that doing it well requires so much extra verbiage that the faux "type-safety" you get doesn't make up for the lost readability. Keep your JavaScript clean, write good tests, and have good code reviews. Otherwise, do all of that but with TypeScript (which, like I said, is a great alternative!).

    BAD CODE:
    ```Javascript
    combine(val1, val2) {
        if (typeof val1 === 'number' && typeof val2 === 'number' ||
            typeof val1 === 'string' && typeof val2 === 'string') {
            return val1 + val2;
        }
        throw new Error('Must be of type String or Number');
    }
    ```

    GOOD CODE:
    ```Javascript
    combine(val1, val2) {
        return val1 + val2;
    }
    ```

12. Remove dead code

    Dead code is just as bad as duplicate code. There's no reason to keep it in your codebase. If it's not being called, get rid of it! It will still be safe in your version history if you still need it.

    BAD CODE:
    ```Javascript
    oldRequestModule(url) {}
    newRequestModule(url) {}

    const req = newRequestModule;
    inventoryTracker('apples', req, 'www.inventory-awesome.io');
    ```

    GOOD CODE:
    ```Javascript
    newRequestModule(url) {}

    const req = newRequestModule;
    inventoryTracker('apples', req, 'www.inventory-awesome.io');
    ```

#### Objects and Data Structures <a name="objectandDSA"></a>

1. Use getters and setters
2. Make objects have private members

#### Classes <a name="classes"></a>

1. Prefer ES2015/ES6 classes over ES5 plain functions
2. Use method chaining
3. Prefer composition over inheritance

#### SOLID <a name="solid"></a>

1. Single Responsibility Principle (SRP)
2. Open/Closed Principle (OCP)
3. Liskov Substitution Principle (LSP)
4. Interface Segregation Principle (ISP)
5. Dependency Inversion Principle (DIP)

#### Testing <a name="testing"></a>

1. Single concept per test

#### Concurrency <a name="concurrency"></a>

1. Use Promises, not callbacks
2. Async/Await are even cleaner than Promises

#### Error Handling <a name="errorhandling"></a>

1. Don't ignore caught errors
2. Don't ignore rejected promises

#### Formatting <a name="formatting"></a>

1. Use consistent capitalization
2. Function callers and callees should be close

#### Comments <a name="comments"></a>

1. Only comment things that have business logic complexity.
2. Don't leave commented out code in your codebase
3. Don't have journal comments
4. Avoid positional markers

[1]: /my-blog/img/portfolio/content5/img1.jpg
[2]: /my-blog/img/portfolio/content5/img2.jpg