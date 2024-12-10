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

![image](https://github.com/user-attachments/assets/09fd22a9-6e3d-4e19-b706-59755441e92d)

For the traffic light pole we use the same code as the traffic light so that it shars the same centre line, but in this case we divide the width by 4 instead of 2, so we get a more narrow rectangle.

![image](https://github.com/user-attachments/assets/ec3bfc22-8939-40d1-bc46-633afac25f00)

![image](https://github.com/user-attachments/assets/300ad055-eb70-4a68-9a4b-fe6aa041f7ff)

![image](https://github.com/user-attachments/assets/6cbde2f8-8f7c-4cf7-838e-57f8ba4a25e8)

![image](https://github.com/user-attachments/assets/b81bb492-3e13-45dc-a79a-733fea6697c8)

![image8](https://github.com/user-attachments/assets/81c513a1-441f-41f8-bf41-365f0cecb1a5) ![image7](https://github.com/user-attachments/assets/9d319379-7a7e-42c9-9229-b5b082642d0e)
![image9](https://github.com/user-attachments/assets/96610782-9982-448d-8bb2-9be553915942)
![image5](https://github.com/user-attachments/assets/cf4fb656-21aa-45b1-88ee-409ca5cd0370)
![image4](https://github.com/user-attachments/assets/5a60d643-0565-45ce-88f6-823b2b38665a)

![image](https://github.com/user-attachments/assets/8052e150-c3bd-41cb-aa41-f50a83ed8d9f)

![image](https://github.com/user-attachments/assets/3469007c-3324-49ae-b5b0-530c0112a4dd)

![image](https://github.com/user-attachments/assets/f5c2a9dd-fd6f-4105-bb41-5292d54f45cf)

![image](https://github.com/user-attachments/assets/d16fba90-2ab2-47d3-afdd-e45aba39c4d0)

![image](https://github.com/user-attachments/assets/499a0226-55fc-43fc-b4c2-abe3e7470921)
