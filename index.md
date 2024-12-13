# **SOC Proejct**
# **Nathan McCormack**
## **Initial Simulation File**
### **Colour cycle Code Simulation**
Here we can see that Red, Blue and Green are set to 1111 when they are on. When two colours are on at the same time, they
create a different colour.

![image](https://github.com/user-attachments/assets/e8a307f0-5cb3-4a2a-a32f-757c5d758eb3)

## **Colour Stripes Code**
When generating the colour stripes, we add in row and coloumn to create the stripes.

![image](https://github.com/user-attachments/assets/d070f62f-18c8-4b1e-9b1b-6b14cc2adf8f)

### **Editing Color Stripes**
Here I have experimented with the rows, columns and colours to gain a better understanidng of how the code works.

![image](https://github.com/user-attachments/assets/3fd7d042-7698-4cd8-926a-f5eaafd40f80)

## **Traffic Light Test**
Here i have created a very basic image which represents a traffic light, with a filter light. Setting the cloumns and rows to certain values i was able to generate small 
blocks with the appropriate colours. I decided to pick a traffic light as it serves as a good strarting point. From here i would like to simulate the ligts turning on in a 
sequence.

![image1](https://github.com/user-attachments/assets/261f1e22-c4a9-4e40-85f0-25ee5301f713)

### **Setting Traffic Light Dimensions**
In the code below i set the dimensions of the screen into variables, and then I divide these variables in half to make the center of the trafic light in the middle of the screen.
I then adjusted the dimensions of the traffic light to make it into a suitable shape.
![image](https://github.com/user-attachments/assets/2c776cc9-c8fa-4246-837b-f33e7cac8913)

Centre_X and Centre_Y are the centre coordanites of the rectangle, the width and height of the traffic light are TRAFFIC_LIGHT_WIDTH and TRAFFIC_LIGHT_HEIGHT. The code divides the height and width by 2 and adds/subtracts the value from the center coordanites to ensure the traffic light is centered and goes an equal distance in each direction. "col>= ... && col<..." ensures that the column values lie between the two boundries and the same code is implemented for rows.

![image](https://github.com/user-attachments/assets/eac66982-cc58-44ac-adeb-02d357817858)


## **Creating Circles for Lights**
For creating the circles we need the following: 
- CENTER__X/Y: We use the same center parameters as the traffic light because we want everything to share the same center line.
- LIGHT_SPACING: This is just the blank space we want in between each light. Using a parameter is easier than using a set value as it prevent mis-inputs which would lead to inaccurate spacing.
- LIGHT_RADIUS: The radius of the circles.

In the if statement we can see some calculations involving rows, columns and other parametres we have, but this can be simplifies into the formula: *(x-h)<sup>2</sup> + (y-k)<sup>2</sup> <= r<sup>2</sup>*. 

Where:
- *(h,k)* is the center of the circle
- *r* is the radius
- *(x,y)* is any point on the plane

In our case:
- *h* = CENTER_X
- *k* = CENTER_X - LIGHT_SPACING (positions circle correctly within the traffic light)
- *x,y* = columns and rows accordingly.

This checks if the squared distance ( *(x-h)<sup>2</sup>* ) from the pixel to the circles center is less than or equal to the squared radius *(r<sup>2</sup>)* of the circle. If it is, the pixel lies within the circle.

I used the same code for the other two circles Green and Amber, but I changed the binary values for red, blue and green to get the desired colours. To simulate the lights being dimmed or turned off i changed the binary value from 1111 to 1010, this halved the value which resulted in a darker colour.

![image](https://github.com/user-attachments/assets/09fd22a9-6e3d-4e19-b706-59755441e92d)

Below is the final output of my project. As you can see there are diferent states, each of which have different light turned ono/off to simulate a real world traffic light sequence. I will explain the code for the sequence.

![image8](https://github.com/user-attachments/assets/81c513a1-441f-41f8-bf41-365f0cecb1a5) 
![image9](https://github.com/user-attachments/assets/96610782-9982-448d-8bb2-9be553915942)
![image5](https://github.com/user-attachments/assets/cf4fb656-21aa-45b1-88ee-409ca5cd0370)
![image4](https://github.com/user-attachments/assets/5a60d643-0565-45ce-88f6-823b2b38665a)

## **Traffic Light Pole**

For the traffic light pole we use the same code as the traffic light so that it shars the same centre line, but in this case we divide the width by 4 instead of 2, so we get a more narrow rectangle. "3'd0/1/2" are a 3-bit representation of the numerical values. I assigned parameter names to these values as it made it more usale for future use.

![image](https://github.com/user-attachments/assets/ec3bfc22-8939-40d1-bc46-633afac25f00)

![image7](https://github.com/user-attachments/assets/9d319379-7a7e-42c9-9229-b5b082642d0e)

## **State Machine**

### **State Definitions**
This code uses localparams to define constants that represent the traffc light sequence. "3'd0/1/2" are a 3-bit representation of the numerical values. I assigned parameter names to these values as it made it more usale for future use. I set the state duration I used "32'd200_000_000" which create a 2 second duration length at a 200MHz clock.

![image](https://github.com/user-attachments/assets/99d235be-9555-4df0-b5ea-e0d46ec7b51a)

### **State Machine Logic**

Here we have a few if statements within an always block. The always block is triggered by the positive dge of the clock or reset signal. This ensures that the sequences occur in sync with the clock, but alos reset when needed.

If(rst)
- The state is set to red. 
- The counter is reset back to 0.

If(counter >= STATE_DURATION)
- The state goes to next state
- The counter resets back to 0

Else (Neither of the if statement are triggered)
- The counter increments by 1 for each clock cycle, this tracks the duration for each state.

![image](https://github.com/user-attachments/assets/2bbeb262-a8e9-477b-9ab9-4bff9504a0b7)

The next state logic is a switch case within an always block. The switch statement takes in the current state and changes the value of "nextState" to the correct state.

![image](https://github.com/user-attachments/assets/a9d566b7-52b5-4180-b8c2-342b3d76fbdf)

Below is the Synthesis Design Schematic, this gives us a detailed view and understanding of the hardware behind the project. We can see our two inputs clk and rst connected to the clock, which is then connected to the two source files VGASync and Colourstripes. When we click into ColourStripes, we can see a detailed view of all the gates used to generate the images.

![image](https://github.com/user-attachments/assets/300ad055-eb70-4a68-9a4b-fe6aa041f7ff)

![image](https://github.com/user-attachments/assets/6cbde2f8-8f7c-4cf7-838e-57f8ba4a25e8)

![image](https://github.com/user-attachments/assets/b81bb492-3e13-45dc-a79a-733fea6697c8)
![image](https://github.com/user-attachments/assets/8052e150-c3bd-41cb-aa41-f50a83ed8d9f)

Here we can see a register, AND gate, Multiplexer, and OR gate. These are all used to control and pass logic states to create my project.

![image](https://github.com/user-attachments/assets/3469007c-3324-49ae-b5b0-530c0112a4dd)
![image](https://github.com/user-attachments/assets/f5c2a9dd-fd6f-4105-bb41-5292d54f45cf)
![image](https://github.com/user-attachments/assets/d16fba90-2ab2-47d3-afdd-e45aba39c4d0)
![image](https://github.com/user-attachments/assets/499a0226-55fc-43fc-b4c2-abe3e7470921)

## **Conclusion**
In this project I started off with a ColourStripes source file which outputted multiple vertical colourd lines, through th eknowledge gained from previous labs and extensive research online, I was able to succesfully create a traffic light simulator which showed multiple images of a traffic light in different sequences. I did this using a state machine. From completing this project, I have a much stronger understanding of SOC concepts, including VGA signal generation and state machine design.
