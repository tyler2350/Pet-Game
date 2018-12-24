# Pet-Game
**Use The Class Build Pet Development Game**

In this project, will write a Python program to **implement a virtual pet**. You can decide the species, name, and gender of your pet. You can also interact with your pet by feeding your pet, playing with your pet, bathing your pet, etc. Will design a user-defined Class called ‘Pet’ to achieve that.

I think a lot of people have played this kind of game like cultivation. It may be a web version, a game console or even a mobile version. So this is my goal, just the initial implementation, without too much optimization and modification.

### Graphical and desktop (Mac Windows Android)
Refer to the Tk part of the python basic manual to program and desktop the program, but for personal reasons will temporarily learn the C++ language. If you are willing to participate or just have this idea and energy, please contact me. I am very happy to work with you.

If you want to develop Android programs you can use Qpython, which is a new supplement package for python.

Perhaps there are still undiscovered problems and errors in the program. If you are lucky enough to be discovered by you, please give me feedback and correct the error. I am very happy to accept.

-------------------

A pet has the following basic attributes:
- Species (we assume two species: dog and cat)
- Name
- Gender (we assume two genders: male and female)
- Fur color

As well as some other attributes that are related to physical or mental health status:
- Energy
- Hunger
- Thirst
- Loneliness
- Smell

These attributes are measured in the range from 0 to 10. For the ‘energy’ attribute, the ideal value is 10. For the other attributes (‘hunger’, ‘thirst’, ‘loneliness’, and ‘smell’), the ideal value is 0. When a pet object is created, his or her initial status is randomized within an acceptable range. For example, a newly created pet may have a hunger/thirst/loneliness/smell level in the range of (0, 5), and have an energy level in the range of (5, 10).

**Therefore, in your pet class, you will have attributes related to each feature that we mentioned. Make them as private attributes (i.e., the attribute name should start with a single underscore)**

-------------------

**Learning Objectives**
- Class

The goal of this game is to take care of your pet by keeping your pet in a good status (i.e., lower hunger/thirst/loneliness/smell level, and higher energy level). You can take care of your pet by taking each of the following actions:
- Let your pet get some sleep
- Feed your pet some food
- Feed your pet some water
- Play with your pet
- Bathe your pet

The health status of your pet will be updated each time you take a certain action:
- After you feed your pet food, his/her hunger level will be decreased.
- After you feed your pet water, his/her thirst level will be decreased.
- After you play with your pet, the loneliness level will be decreased, but the hunger level, thirst level, and smell level will be increased.
- After you bathe your pet, the smell level will be decreased.
- After your pet gets some sleep, the energy level will be increased.

After you take an action, your pet will give you feedback about the specific action you took. Next, your pet will report his/her status if some attributes are too low or too high. For example, after you play with your pet, your pet will first say ‘Thanks for your company’. Next, if the hunger level of your pet is lower than a threshold (say 5), your pet will say ‘I am hungry’. Please note that multiple attributes may need to be reported after an action. If your pet is both hungry and thirsty after playing with you, he/she will say two sentences: ‘I am hungry,’ and then ‘I am thirsty’.

The game begins by prompting you to entering the species, name, gender, and fur color of your pet, each feature separated by a space. Once those inputs are validated, a pet object will be created. Then the program will prompt you to enter a command. Your command will either lead to an action taken or lead to a table that shows you the health status of your pet. The program will repeatedly prompt you to input a command, until you enter ‘q’ and then you will quit this game.

-------------------

**Project Specifications**

Design a class called **Pet** which initialize the following attributes in its __init__() function:
- self._name               # string
- self._species            # string
- self._gender             # string
- self._color              # string
- self._hunger             # float
- self._thirst             # float
- self._smell              # float
- self._loneliness         # float
- self._energy             # float
- self._edible_items       # list
- self._drinkable_items    # list

To fill in appropriate values for initialization:
- The default values for **name, species, gender,** and **color** are **'Fluffy', 'Dog', 'Male',** and **'White'** respectively. Force the attribute values to be capitalized (use the **capitalize()** string method).
- The initial value for **hunger, thirst, smell,** and **loneliness** are a random integer number in the range of [0, 5], while the initial value for **energy** is a random integer number in the range of [5, 10].
- The initial value for **_edible_items**_ and **_drinkable_items**_ is an empty list. (We will append some items to these lists later on, so that **_edible_items**_ and **_drinkable_items**_ will be a list of different class types, and each class type is provided in the **edible.py** file. An example of a list of class types is given here: **a_list = [str, int, float]**)

After initialize the attributes mentioned above, there is a call to the **_reply_to_master**_ method.

**def get_hunger_level(self)**: simply return the value of **self._hunger**_

**def get_thirst_level(self)**: similar to previous.

**def get_energy_level(self)**: similar to previous.

**def drink(self, liquid)**: this method represents the action of ‘feeding water’.
- this method takes an input parameter called **liquid**, which is an instance that belongs to a certain class type. This class type should be an element in the **self._drinkable_items**_ list. (For example, if liquid = 1 (or any other integer), then **int** must be an element in the **self._drinkable_items**_ list.) Otherwise, your program will output an error message. (use isinstance() function).
- Call the **_time_pass_by**_ method with the default time (which is complete and does not need modification).
- If the liquid is valid, you will decrease the **thirsty** value of your pet, based on the quantity of this liquid. You must make sure that your pet’s thirst level will not go below zero. For example, if the **_thirst**_ value is 3, and the quantity of the liquid is 2, then after you call the drink function, **_thirst**_ will be 1. If the quantity of the liquid is 4, then **_thirst**_ will become 0, not -1. If all the liquid is not drunk, print **"Too much drink to finish. I will leave some for you."**
- A pet will not drink if their thirst is less than 2. If they will not drink, print a message, e.g. **"Your pet is satisfied, no desire for sustenance now."** if they are not hungry.
- If the liquid is invalid, print **"Not drinkable"**
- After you update the **_thirst**_ value, call the **_reply_to_master()**_ method.

**def feed(self, food)**: the logic of this method is very similar to drink. The difference is that in this method, you will update the value of **_hunger**_. You will also call the **_reply_to_master()**_ method with a different input argument than used with drink.
