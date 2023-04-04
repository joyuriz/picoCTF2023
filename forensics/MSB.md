# forensics/MSB
Write-up by: [ptrckstuns](https://github.com/ptrckstuns)

## Description
This image passes LSB statistical analysis, but we can't help but think there must be something to the visual artifacts present in this image... 
Download the image here

![Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada.flag.png](/attachments/Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada.flag.png)

Official Hint:
> "What's causing the 'corruption' of the image?"

## Solution:
1. Use [Stegsolve](http://www.caesum.com/handbook/Stegsolve.jar) to analyze the image.
2. Open the PNG file in Stegsolve.jar and analyze
3. The text is readable with these Bit Planes and **MSB** Bit Order
   ![](/attachments/stegsolve1.png)
   > Note: RGB - 777 is important

   > Save Text for faster searching of strings.
4. Search the "pico" string
   ![](/attachments/stegsolve2.png)

**Flag:** `picoCTF{15_y0ur_que57_qu1x071c_0r_h3r01c_24d55bee}`