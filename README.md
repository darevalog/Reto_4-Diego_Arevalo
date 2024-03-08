# Reto_4-Diego_Arevalo
## Solución del reto cuatro de Programación Orientada a Objetos 

### 1. `RESTAURANT SCENARIO`
This code shows you the menu of a restaurant and allows you to choose the products to be consumed, calculate their value, generate a discount and select the payment method. 

```python
import os
os.system("cls")

class menuitem:
    def __init__(self, name, price):
        self.name = name
        self.price = price

class  appetizer(menuitem):
    def __init__(self, name, price, calories):
        super().__init__(name, price)
        self.calories = calories

    def __str__(self):
        return f"{self.name}: ${self.price} ({self.calories} cal)"
    
class main_course(menuitem):
    def __init__(self, name, price, calories, protein):
        super().__init__(name, price)
        self.calories = calories
        self.protein = protein

    def __str__(self):
        return f"{self.name}: ${self.price} ({self.calories} cal, {self.protein} g)"

class beverage(menuitem):
    def __init__(self, name, price, volume):
        super().__init__(name, price)
        self.volume = volume

    def __str__(self):
        return f"{self.name}: ${self.price} ({self.volume} ml)"
    
class order(menuitem):
    def __init__(self):
        self.items = []

    def add_item(self, item):
        self.items.append(item)

    def calculate_total(self):
        total = 0
        for item in self.items:
            total += item.price
        return total

    def apply_discount(self):
        discount = 0.1
        total = self.calculate_total()
        discounted_total = total - (total * discount)
        return discounted_total
    
class payment_method:
    def __init__(self):
        pass

    def pay(self, amount):
        pass

class credit_card(payment_method):
    def __init__(self, number, expiration_date, cvv):
        super().__init__()
        self.number = number
        self.expiration_date = expiration_date
        self.cvv = cvv

    def pay(self, amount):
        print(f"\nPaid ${amount} with credit card numbered ********{self.number[-4:]}.\n")

class cash(payment_method):
    def __init__(self, amount):
        super().__init__()
        self.amount = amount

    def pay(self, amount):
        print(f"\nPaid ${amount} with cash and they have been returned ${round(cash_amount - amount, 2)}.\n")
    
# Creación de menú
appetizer1 = appetizer("Guacamole", 5.50, 150)
appetizer2 = appetizer("Nachos", 6.50, 200)
appetizer3 = appetizer("Queso fundido", 7.50, 250)
appetizer4 = appetizer("Tostadas", 4.50, 100)
main_course1 = main_course("Tacos", 12.50, 300, 20)
main_course2 = main_course("Burrito", 10.50, 400, 25)
main_course3 = main_course("Enchiladas", 11.50, 350, 22)
main_course4 = main_course("Quesadillas", 9.50, 250, 18)
beverage1 = beverage("Margarita", 8.50, 250)
beverage2 = beverage("Tequila", 7.50, 200)
beverage3 = beverage("Soda", 2.50, 500)
beverage4 = beverage("Water", 1.50, 500)

a = " MENU "
b = a.center(50, "-")
print(b)
print("\nAppetizers:")
print(appetizer1)
print(appetizer2)
print(appetizer3)
print(appetizer4)
print("\nMain courses:")
print(main_course1)
print(main_course2)
print(main_course3)
print(main_course4)
print("\nBeverages:")
print(beverage1)
print(beverage2)
print(beverage3)
print(beverage4)
print()


# Creación de orden por input del cliente
order1 = order()

while True:
    c = " ORDER "
    d = c.center(50, "-")
    print(d)
    print()
    print("1. Add appetizer")
    print("2. Add main course")
    print("3. Add beverage")
    print("4. Finish order")
    choice = input("\nEnter your choice: ")

    if choice == "1":
        print("\nAppetizers:")
        print("1. Guacamole")
        print("2. Nachos")
        print("3. Queso fundido")
        print("4. Tostadas")
        appetizer_choice = input("\nEnter appetizer choice: ")
        print()

        if appetizer_choice == "1":
            order1.add_item(appetizer1)
        elif appetizer_choice == "2":
            order1.add_item(appetizer2)
        elif appetizer_choice == "3":
            order1.add_item(appetizer3)
        elif appetizer_choice == "4":
            order1.add_item(appetizer4)
        else:
            print("\nInvalid choice. Please try again.\n")

    elif choice == "2":
        print("\nMain courses:")
        print("1. Tacos")
        print("2. Burrito")
        print("3. Enchiladas")
        print("4. Quesadillas")
        main_course_choice = input("\nEnter main course choice: ")
        print()

        if main_course_choice == "1":
            order1.add_item(main_course1)
        elif main_course_choice == "2":
            order1.add_item(main_course2)
        elif main_course_choice == "3":
            order1.add_item(main_course3)
        elif main_course_choice == "4":
            order1.add_item(main_course4)
        else:
            print("\nInvalid choice. Please try again.\n")

    elif choice == "3":
        print("\nBeverages:")
        print("1. Margarita")
        print("2. Tequila")
        print("3. Soda")
        print("4. Water")
        beverage_choice = input("\nEnter beverage choice: ")
        print()

        if beverage_choice == "1":
            order1.add_item(beverage1)
        elif beverage_choice == "2":
            order1.add_item(beverage2)
        elif beverage_choice == "3":
            order1.add_item(beverage3)
        elif beverage_choice == "4":
            order1.add_item(beverage4)
        else:
            print("\nInvalid choice. Please try again.\n")

    elif choice == "4":
        print("\nOrder complete.\n")
        break  

    else:
        print("\nInvalid choice. Please try again.\n")

e = " FINAL ORDER "
f = e.center(50, "-")
print(f)
print()
for item in order1.items:
    print(item)
print(f"\nTotal: ${order1.calculate_total()}")
print(f"Total with discount: ${order1.apply_discount()} (10% of discount)\n")

# Defie a payment method
while True:
    g = " PAYMENT METHOD "
    h = g.center(50, "-")
    print(h)
    print()
    print("1. Credit card")
    print("2. Cash")
    payment_choice = input("\nEnter payment choice: ")
    print()

    if payment_choice == "1":
        credit_card_number = input("Enter credit card number: ")
        expiration_date = input("Enter expiration date: ")
        cvv = input("Enter CVV: ")
        payment1 = credit_card(credit_card_number, expiration_date, cvv)
        payment1.pay(order1.apply_discount())
        break

    elif payment_choice == "2":
        cash_amount = float(input("Enter cash amount: "))
        payment2 = cash(cash_amount)
        payment2.pay(order1.apply_discount())
        break

    else:
        print("\nInvalid choice. Please try again.\n")
```

### 2. `SHAPE CREATOR `
This code allows you to create a set of regular and irregular polygons, including rectangles, squares and triangles (with their different derivations).

```python
import math
import os

os.system("cls")

class point:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def compute_distance(self, point):
        return ((self.x - point.x)**2 + (self.y - point.y)**2)**0.5
    
class line(point):
    def __init__(self, start_point, end_point, length):
        self.start_point = start_point
        self.end_point = end_point
        self.length = length

class shape:
    def __init__(self, is_regular):
        self.is_regular = is_regular

    def vertices(self):
        pass

    def edges(self):
        pass

    def inner_angle(self):
        pass

    def compute_area(self):
        pass
        
    def compute_perimeter(self):
        pass

    def compute_inner_angle(self):
        pass

class rectangle(shape):
    def __init__(self, width, height, center):
        self.width = width
        self.height = height
        self.center = center
        self.is_regular = True

    def vertices(self):
        point1 = point(self.center.x - self.width/2, self.center.y - self.height/2)  
        point2 = point(self.center.x + self.width/2, self.center.y - self.height/2)
        point3 = point(self.center.x + self.width/2, self.center.y + self.height/2)
        point4 = point(self.center.x - self.width/2, self.center.y + self.height/2)
        print(f"Vertices (points): {point1.x, point1.y}, {point2.x, point2.y}, {point3.x, point3.y}, {point4.x, point4.y}")

    def edges(self):
        edge1 = line(point(self.center.x - self.width/2, self.center.y - self.height/2), point(self.center.x + self.width/2, self.center.y - self.height/2), self.width)
        edge2 = line(point(self.center.x + self.width/2, self.center.y - self.height/2), point(self.center.x + self.width/2, self.center.y + self.height/2), self.height)
        edge3 = line(point(self.center.x + self.width/2, self.center.y + self.height/2), point(self.center.x - self.width/2, self.center.y + self.height/2), self.width)
        edge4 = line(point(self.center.x - self.width/2, self.center.y + self.height/2), point(self.center.x - self.width/2, self.center.y - self.height/2), self.height)
        print(f"Edges (lengths): {(edge1.length, edge2.length), (edge2.length, edge3.length), (edge3.length, edge4.length), (edge4.length, edge1.length)}")

    def compute_area(self):
        return round(self.width * self.height, 2)

    def compute_perimeter(self):
        return round(2 * self.width + 2 * self.height, 2)

    def compute_inner_angle(self):
        return 90, 90, 90, 90
    
class square(rectangle):
    def __init__(self, side, center):
        self.side = side
        self.center = center
        self.is_regular = True
        
    def vertices(self):
        point1 = point(self.center.x - self.side/2, self.center.y - self.side/2)  
        point2 = point(self.center.x + self.side/2, self.center.y - self.side/2)
        point3 = point(self.center.x + self.side/2, self.center.y + self.side/2)
        point4 = point(self.center.x - self.side/2, self.center.y + self.side/2)
        print(f"Vertices (points): {point1.x, point1.y}, {point2.x, point2.y}, {point3.x, point3.y}, {point4.x, point4.y}")
    
    def edges(self):
        edge1 = line(point(self.center.x - self.side/2, self.center.y - self.side/2), point(self.center.x + self.side/2, self.center.y - self.side/2), self.side)
        edge2 = line(point(self.center.x + self.side/2, self.center.y - self.side/2), point(self.center.x + self.side/2, self.center.y + self.side/2), self.side)
        edge3 = line(point(self.center.x + self.side/2, self.center.y + self.side/2), point(self.center.x - self.side/2, self.center.y + self.side/2), self.side)
        edge4 = line(point(self.center.x - self.side/2, self.center.y + self.side/2), point(self.center.x - self.side/2, self.center.y - self.side/2), self.side)
        print(f"Edges (lengths): {(edge1.length, edge2.length), (edge2.length, edge3.length), (edge3.length, edge4.length), (edge4.length, edge1.length)}")
    
    def compute_area(self):
        return round(self.side**2, 2)

    def compute_perimeter(self):
        return round(4 * self.side, 2)

    def compute_inner_angle(self):
        return 90, 90, 90, 90

class triangle(shape):
    def __init__(self, is_regular):
        self.is_regular = is_regular

    def vertices(self):
        return 3

    def edges(self):
        return 3

    def inner_angle(self):
        pass
    
class isoceles(triangle):
    def __init__(self, side1, side2, center):
        self.side1 = side1
        self.side2 = side2
        self.side3 = side2
        self.center = center
        self.is_regular = False

    def vertices(self):
        point1 = point(self.center.x, self.center.y + self.side1)
        point2 = point(self.center.x - self.side2/2, self.center.y - self.side1/2)
        point3 = point(self.center.x + self.side2/2, self.center.y - self.side1/2)
        print(f"Vertices (points): {point1.x, point1.y}, {point2.x, point2.y}, {point3.x, point3.y}")
    
    def edges(self):
        edge1 = line(point(self.center.x, self.center.y + self.side1), point(self.center.x - self.side2/2, self.center.y - self.side1/2), self.side1)
        edge2 = line(point(self.center.x - self.side2/2, self.center.y - self.side1/2), point(self.center.x + self.side2/2, self.center.y - self.side1/2), self.side2)
        edge3 = line(point(self.center.x + self.side2/2, self.center.y - self.side1/2), point(self.center.x, self.center.y + self.side1), self.side1)
        print(f"Edges (lengths): {(edge1.length, edge2.length), (edge2.length, edge3.length), (edge3.length, edge1.length)}")
    
    def compute_area(self):
        s = (self.side1 + self.side2 + self.side3) / 2
        return round(math.sqrt(s * (s - self.side1) * (s - self.side2)), 2)

    def compute_perimeter(self):
        return round(2 * self.side1 + self.side2, 2)

    def compute_inner_angle(self):
        angle1 = round(math.degrees(math.acos((self.side1**2 + self.side2**2 - self.side3**2)/(2 * self.side1 * self.side2))), 2)
        angle2 = angle1
        angle3 = 180 - 2 * angle1
        return angle1, angle2, angle3
    
class equilateral(triangle):
    def __init__(self, side, center):
        self.side = side
        self.center = center
        self.is_regular = True

    def vertices(self):
        point1 = point(self.center.x, self.center.y + self.side)
        point2 = point(self.center.x - self.side/2, self.center.y)
        point3 = point(self.center.x + self.side/2, self.center.y)
        print(f"Vertices (points): {point1.x, point1.y}, {point2.x, point2.y}, {point3.x, point3.y}")
    
    def edges(self):
        edge1 = line(point(self.center.x, self.center.y + self.side), point(self.center.x - self.side/2, self.center.y), self.side)
        edge2 = line(point(self.center.x - self.side/2, self.center.y), point(self.center.x + self.side/2, self.center.y), self.side)
        edge3 = line(point(self.center.x + self.side/2, self.center.y), point(self.center.x, self.center.y + self.side), self.side)
        print(f"Edges (lengths): {(edge1.length, edge2.length), (edge2.length, edge3.length), (edge3.length, edge1.length)}")
    
    def compute_area(self):
        s = self.compute_perimeter() / 2
        return round(math.sqrt(s * (s - self.side) * (s - self.side) * (s - self.side)), 2)

    def compute_perimeter(self):
        return round(3 * self.side, 2)

    def compute_inner_angle(self):
        return 60, 60, 60
    
class scalene(triangle):
    def __init__(self, side1, side2, side3, center):
        self.side1 = side1
        self.side2 = side2
        self.side3 = side3
        self.center = center
        self.is_regular = False

    def vertices(self):
        point1 = point(self.center.x, self.center.y + self.side1)
        point2 = point(self.center.x - self.side2/2, self.center.y - self.side1/2)
        point3 = point(self.center.x + self.side2/2, self.center.y - self.side1/2)
        print(f"Vertices (points): {point1.x, point1.y}, {point2.x, point2.y}, {point3.x, point3.y}")
    
    def edges(self):
        edge1 = line(point(self.center.x, self.center.y + self.side1), point(self.center.x - self.side2/2, self.center.y - self.side1/2), self.side1)
        edge2 = line(point(self.center.x - self.side2/2, self.center.y - self.side1/2), point(self.center.x + self.side2/2, self.center.y - self.side1/2), self.side2)
        edge3 = line(point(self.center.x + self.side2/2, self.center.y - self.side1/2), point(self.center.x, self.center.y + self.side1), self.side1)
        print(f"Edges (lengths): {(edge1.length, edge2.length), (edge2.length, edge3.length), (edge3.length, edge1.length)}")
    
    def compute_area(self):
        s = self.compute_perimeter() / 2
        return round(math.sqrt(s * (s - self.side1) * (s - self.side2) * (s - self.side3)), 2)

    def compute_perimeter(self):
        return round(self.side1 + self.side2 + self.side3, 2)

    def compute_inner_angle(self):
        angle1 = round(math.degrees(math.acos((self.side1**2 - self.side2**2 + self.side3**2)/(2 * self.side1 * self.side3))), 2)
        angle2 = round(math.degrees(math.acos((self.side2**2 - self.side1**2 + self.side3**2)/(2 * self.side2 * self.side3))), 2)
        angle3 = 180 - angle1 - angle2
        return angle1, angle2, angle3
    
class TriRectangle(triangle):
    def __init__(self, opposite, adjacent, hypotenuse, center):
        self.opposite = opposite
        self.adjacent = adjacent
        self.hypotenuse = hypotenuse
        self.center = center   
        self.is_regular = False

    def vertices(self):
        point1 = point(self.center.x, self.center.y + self.opposite)
        point2 = point(self.center.x - self.adjacent/2, self.center.y - self.opposite/2)
        point3 = point(self.center.x + self.adjacent/2, self.center.y - self.opposite/2)
        print(f"Vertices (points): {point1.x, point1.y}, {point2.x, point2.y}, {point3.x, point3.y}")
    
    def edges(self):
        edge1 = line(point(self.center.x, self.center.y + self.opposite), point(self.center.x - self.adjacent/2, self.center.y - self.opposite/2), self.opposite)
        edge2 = line(point(self.center.x - self.adjacent/2, self.center.y - self.opposite/2), point(self.center.x + self.adjacent/2, self.center.y - self.opposite/2), self.adjacent)
        edge3 = line(point(self.center.x + self.adjacent/2, self.center.y - self.opposite/2), point(self.center.x, self.center.y + self.opposite), self.hypotenuse)
        print(f"Edges (lengths  ): {(edge1.length, edge2.length), (edge2.length, edge3.length), (edge3.length, edge1.length)}")
    
    def compute_area(self):
        return round(0.5 * self.opposite * self.adjacent, 2)

    def compute_perimeter(self):
        return round(self.opposite + self.adjacent + self.hypotenuse, 2)
    
    def compute_inner_angle(self):
        angle1 = round(math.degrees(math.acos(self.opposite/self.hypotenuse)), 2)
        angle2 = round(math.degrees(math.acos(self.adjacent/self.hypotenuse)), 2)
        angle3 = 90
        return angle1, angle2, angle3
    

# Create a shape from user input
str = " SHAPE CREATOR "
print(str.center(70, "-"))
figure = input("\nEnter the shape type (rectangle, square, triangle): ")

if figure == "rectangle":
    width = float(input("\nEnter the width of the rectangle: "))
    height = float(input("\nEnter the height of the rectangle: "))
    center = point(float(input("\nEnter the x coordinate of the center: ")), float(input("\nEnter the y coordinate of the center: ")))
    shape_obj = rectangle(width, height, center)

elif figure == "square":
    side = float(input("\nEnter the side length of the square: "))
    center = point(float(input("\nEnter the x coordinate of the center: ")), float(input("\nEnter the y coordinate of the center: ")))
    shape_obj = square(side, center)

elif figure == "triangle":
    triangle_type = input("\nEnter the triangle type (isoceles, equilateral, scalene, rectangular): ")

    if triangle_type == "isoceles":
        side1 = float(input("\nEnter the length of side 1: "))
        side2 = float(input("\nEnter the length of side 2: "))
        center = point(float(input("\nEnter the x coordinate of the center: ")), float(input("\nEnter the y coordinate of the center: ")))
        shape_obj = isoceles(side1, side2, center)

    elif triangle_type == "equilateral":
        side = float(input("\nEnter the side length: "))
        center = point(float(input("\nEnter the x coordinate of the center: ")), float(input("\nEnter the y coordinate of the center: ")))
        shape_obj = equilateral(side, center)

    elif triangle_type == "scalene":
        side1 = float(input("\nEnter the length of side 1: "))
        side2 = float(input("\nEnter the length of side 2: "))
        side3 = float(input("\nEnter the length of side 3: "))
        center = point(float(input("\nEnter the x coordinate of the center: ")), float(input("\nEnter the y coordinate of the center: ")))
        shape_obj = scalene(side1, side2, side3, center)

    elif triangle_type == "rectangular":
        opposite = float(input("\nEnter the length of the opposite side: "))
        adjacent = float(input("\nEnter the length of the adjacent side: "))
        hypotenuse = float(input("\nEnter the length of the hypotenuse: "))
        center = point(float(input("\nEnter the x coordinate of the center: ")), float(input("\nEnter the y coordinate of the center: ")))
        shape_obj = TriRectangle(opposite, adjacent, hypotenuse, center)

    else:
        print("\nInvalid triangle type")

else:
    print("\nInvalid shape type")

print("\nShape created:", figure)
print("Area:", round(shape_obj.compute_area(), 2))
print("Perimeter:", round(shape_obj.compute_perimeter(), 2))
print("Inner Angles:", tuple(round(angle, 2) for angle in shape_obj.compute_inner_angle()))
shape_obj.vertices()
shape_obj.edges()
print()
```
> :shipit: Diego Alejandro Arévalo Guevara. March 07, 2024.
