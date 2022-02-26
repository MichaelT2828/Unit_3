# Calculator

### Python Code

```.py
from kivymd.app import MDApp
from kivymd.uix.screen import MDScreen
from kivy.uix.textinput import TextInput

class calculator(MDApp):
    def __init__(self, **kwargs):
        super().__init__(**kwargs)
        self.first_input = 0
        self.second_input = 0
        self.operator = ''

    def reset(self):
        self.first_input = 0
        self.second_input = 0
        self.root.ids.number_label.text = "0"

    ''' These methods take input from the number buttons'''
    def zero(self):
        if self.root.ids.number_label.text == "0":
            self.root.ids.number_label.text = '0'
        elif self.root.ids.number_label.text != "0":
            self.root.ids.number_label.text += '0'

    def one(self):
        if self.root.ids.number_label.text == "0":
            self.root.ids.number_label.text = '1'
        elif self.root.ids.number_label.text != "0":
            self.root.ids.number_label.text += '1'

    def two(self):
        if self.root.ids.number_label.text == "0":
            self.root.ids.number_label.text = '2'
        elif self.root.ids.number_label.text != "0":
            self.root.ids.number_label.text += '2'

    def three(self):
        if self.root.ids.number_label.text == "0":
            self.root.ids.number_label.text = '3'
        elif self.root.ids.number_label.text != "0":
            self.root.ids.number_label.text += '3'

    def four(self):
        if self.root.ids.number_label.text == "0":
            self.root.ids.number_label.text = '4'
        elif self.root.ids.number_label.text != "0":
            self.root.ids.number_label.text += '4'

    def five(self):
        if self.root.ids.number_label.text == "0":
            self.root.ids.number_label.text = '5'
        elif self.root.ids.number_label.text != "0":
            self.root.ids.number_label.text += '5'

    def six(self):
        if self.root.ids.number_label.text == "0":
            self.root.ids.number_label.text = '6'
        elif self.root.ids.number_label.text != "0":
            self.root.ids.number_label.text += '6'

    def seven(self):
        if self.root.ids.number_label.text == "0":
            self.root.ids.number_label.text = '7'
        elif self.root.ids.number_label.text != "0":
            self.root.ids.number_label.text += '7'

    def eight(self):
        if self.root.ids.number_label.text == "0":
            self.root.ids.number_label.text = '8'
        elif self.root.ids.number_label.text != "0":
            self.root.ids.number_label.text += '8'

    def nine(self):
        if self.root.ids.number_label.text == "0":
            self.root.ids.number_label.text = '9'
        elif self.root.ids.number_label.text != "0":
            self.root.ids.number_label.text += '9'

    ''' These methods do math operations'''
    def add(self):
        if self.root.ids.number_label.text[-1] not in '+-*÷':
            self.root.ids.number_label.text += "+"
        elif self.root.ids.number_label.text[-1] in '+-*÷':
            temp = list(self.root.ids.number_label.text)
            temp[-1] = "+"
            self.root.ids.number_label.text = ''.join(temp)

    def subtract(self):
        if self.root.ids.number_label.text[-1] not in '+-*÷':
            self.root.ids.number_label.text += "-"
        elif self.root.ids.number_label.text[-1] in '+-*÷':
            temp = list(self.root.ids.number_label.text)
            temp[-1] = "-"
            self.root.ids.number_label.text = ''.join(temp)

    def multiply(self):
        if self.root.ids.number_label.text[-1] not in '+-*÷':
            self.root.ids.number_label.text += "*"
        elif self.root.ids.number_label.text[-1] in '+-*÷':
            temp = list(self.root.ids.number_label.text)
            temp[-1] = "*"
            self.root.ids.number_label.text = ''.join(temp)

    def divide(self):
        if self.root.ids.number_label.text[-1] not in '+-*÷':
            self.root.ids.number_label.text += "/"
        elif self.root.ids.number_label.text[-1] in '+-*÷':
            temp = list(self.root.ids.number_label.text)
            temp[-1] = "/"
            self.root.ids.number_label.text = ''.join(temp)

    def negative(self):
        if self.root.ids.number_label.text[0] != '-':
            self.root.ids.number_label.text = "-" + self.root.ids.number_label.text
        elif self.root.ids.number_label.text[0] == '-':
            temp = list(self.root.ids.number_label.text)
            temp[0] = " "
            self.root.ids.number_label.text = ''.join(temp)

    def decimal(self):
        if self.root.ids.number_label.text[-1] not in '+-*÷':
            self.root.ids.number_label.text += "."

    def percent(self):
        if '+-*÷' not in self.root.ids.number_label.text:
            temp = float(self.root.ids.number_label.text)
            self.root.ids.number_label.text = str(temp/100)

    def execute(self):
        self.root.ids.number_label.text = str(round(eval(self.root.ids.number_label.text), 7))

    def first_input(self):
        print("User clicked first input number")

    def build(self):
        return

calculator = calculator()
calculator.run()
```

### kivy Code

```.kv
Screen:
    size: 500, 800

    MDBoxLayout:
        orientation: "vertical"
        size_hint: 1, 1

        MDLabel: # space gap between top of window and number display
            size_hint: 1, 0.1

        MDBoxLayout:
            orientation: "horizontal"
            size_hint: 1, 0.2

            MDLabel: # number display
                id: number_label
                text: "0"
                halign: "right"
                font_size: "64pt"
                size_hint: 1, 0.8


            MDLabel: # space gap between number display and right size of window
                size_hint: 0.11, 1

        MDBoxLayout:
            orientation: "horizontal"
            size_hint: 1, 0.1

            MDLabel: # signature
                id: signature_label
                text: "A calculator by Michael Tseng"
                halign: "right"
                font_size: "10pt"
                size_hint: 1, 1

            MDLabel: # space gap between signature and right size of window
                size_hint: 0.11, 1

        MDBoxLayout: # top layer of buttons
            orientation: "horizontal"
            size_hint: 1, 0.2

            MDLabel: # space gap between left side of window and bottom layer of buttons
                size_hint: 0.1, 1

            MDRaisedButton:
                id: reset_button
                size_hint: 0.2, 1
                text: "AC"
                font_size: "32pt"
                md_bg_color: 230/255, 215/255, 171/255, 1
                on_release:
                    app.reset()

            MDLabel:
                size_hint: 0.00666, 1

            MDRaisedButton:
                id: negative_button
                size_hint: 0.2, 1
                text: "+/-"
                font_size: "32pt"
                md_bg_color: 230/255, 215/255, 171/255, 1
                on_release:
                    app.negative()

            MDLabel:
                size_hint: 0.00666, 1

            MDRaisedButton:
                id: percent_button
                size_hint: 0.2, 1
                text: "%"
                font_size: "32pt"
                md_bg_color: 230/255, 215/255, 171/255, 1
                on_release:
                    app.percent()

            MDLabel:
                size_hint: 0.00666, 1

            MDRaisedButton:
                id: divide_button
                size_hint: 0.2, 1
                text: "÷"
                font_size: "32pt"
                md_bg_color: 229/255, 155/255, 59/255, 1
                on_release:
                    app.divide()

            MDLabel: # space gap between right side of window and buttons
                size_hint: 0.1, 1

        MDLabel: # space gap between buttons
            size_hint: 1, 0.011

        MDBoxLayout: # second top layer of buttons
            orientation: "horizontal"
            size_hint: 1, 0.2

            MDLabel: # space gap between left side of window and bottom layer of buttons
                size_hint: 0.1, 1

            MDRaisedButton:
                id: seven_button
                size_hint: 0.2, 1
                text: "7"
                font_size: "32pt"
                md_bg_color: 0, 0, 0, 1
                on_release:
                    app.seven()

            MDLabel:
                size_hint: 0.00666, 1

            MDRaisedButton:
                id: eight_button
                size_hint: 0.2, 1
                text: "8"
                font_size: "32pt"
                md_bg_color: 0, 0, 0, 1
                on_release:
                    app.eight()

            MDLabel:
                size_hint: 0.00666, 1

            MDRaisedButton:
                id: nine_button
                size_hint: 0.2, 1
                text: "9"
                font_size: "32pt"
                md_bg_color: 0, 0, 0, 1
                on_release:
                    app.nine()

            MDLabel:
                size_hint: 0.00666, 1

            MDRaisedButton:
                id: multiply_button
                size_hint: 0.2, 1
                text: "×"
                font_size: "32pt"
                md_bg_color: 229/255, 155/255, 59/255, 1
                on_release:
                    app.multiply()

            MDLabel: # space gap between right side of window and buttons
                size_hint: 0.1, 1

        MDLabel: # space gap between buttons
            size_hint: 1, 0.011

        MDBoxLayout: # second top layer of buttons
            orientation: "horizontal"
            size_hint: 1, 0.2

            MDLabel: # space gap between left side of window and bottom layer of buttons
                size_hint: 0.1, 1

            MDRaisedButton:
                id: four_button
                size_hint: 0.2, 1
                text: "4"
                font_size: "32pt"
                md_bg_color: 0, 0, 0, 1
                on_release:
                    app.four()

            MDLabel:
                size_hint: 0.00666, 1

            MDRaisedButton:
                id: five_button
                size_hint: 0.2, 1
                text: "5"
                font_size: "32pt"
                md_bg_color: 0, 0, 0, 1
                on_release:
                    app.five()

            MDLabel:
                size_hint: 0.00666, 1

            MDRaisedButton:
                id: six_button
                size_hint: 0.2, 1
                text: "6"
                font_size: "32pt"
                md_bg_color: 0, 0, 0, 1
                on_release:
                    app.six()

            MDLabel:
                size_hint: 0.00666, 1

            MDRaisedButton:
                id: subtract_button
                size_hint: 0.2, 1
                text: "-"
                font_size: "32pt"
                md_bg_color: 229/255, 155/255, 59/255, 1
                on_release:
                    app.subtract()

            MDLabel: # space gap between right side of window and buttons
                size_hint: 0.1, 1

        MDLabel: # space gap between buttons
            size_hint: 1, 0.011

        MDBoxLayout: # second bottom layer of buttons
            orientation: "horizontal"
            size_hint: 1, 0.2

            MDLabel: # space gap between left side of window and buttons
                size_hint: 0.1, 1

            MDRaisedButton:
                id: one_button
                size_hint: 0.2, 1
                text: "1"
                font_size: "32pt"
                md_bg_color: 0, 0, 0, 1
                on_release:
                    app.one()

            MDLabel:
                size_hint: 0.00666, 1

            MDRaisedButton:
                id: two_button
                size_hint: 0.2, 1
                text: "2"
                font_size: "32pt"
                md_bg_color: 0, 0, 0, 1
                on_release:
                    app.two()

            MDLabel:
                size_hint: 0.00666, 1

            MDRaisedButton:
                id: three_button
                size_hint: 0.2, 1
                text: "3"
                font_size: "32pt"
                md_bg_color: 0, 0, 0, 1
                on_release:
                    app.three()

            MDLabel:
                size_hint: 0.00666, 1

            MDRaisedButton:
                id: add_button
                size_hint: 0.2, 1
                text: "+"
                font_size: "32pt"
                md_bg_color: 229/255, 155/255, 59/255, 1
                on_release:
                    app.add()

            MDLabel: # space gap between right side of window and buttons
                size_hint: 0.1, 1

        MDLabel: # space gap between buttons
            size_hint: 1, 0.011

        MDBoxLayout: # bottom layer of buttons
            orientation: "horizontal"
            size_hint: 1, 0.2

            MDLabel: # space gap between left side of window and buttons
                size_hint: 0.1, 1

            MDRaisedButton:
                id: zero_button
                size_hint: 0.40666, 1
                text: "0"
                font_size: "32pt"
                md_bg_color: 0, 0, 0, 1
                on_release:
                    app.zero()

            MDLabel:
                size_hint: 0.00666, 1

            MDRaisedButton:
                id: decimal_button
                size_hint: 0.2, 1
                text: "."
                font_size: "32pt"
                md_bg_color: 0, 0, 0, 1
                on_release:
                    app.decimal()

            MDLabel:
                size_hint: 0.00666, 1

            MDRaisedButton:
                id: equal_button
                size_hint: 0.2, 1
                text: "="
                font_size: "32pt"
                md_bg_color: 229/255, 155/255, 59/255, 1
                on_release:
                    app.execute()

            MDLabel: # space gap between right side of window and buttons
                size_hint: 0.1, 1

        MDLabel: # space gap between bottom of window and bottom layer of buttons
            size_hint: 1, 0.15
```

### Test

https://github.com/MichaelT2828/Unit_3/blob/main/Homework/calculator_test.mov
