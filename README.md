# HyperDisplayFonts
Font support for the SparkFun HyperDisplay library.

Overview:
The HyperDisplay library designed for the SparkFun line of displays is great for drawing graphics to the screen, 
however, font support is limited to small characters, oriented in a single direction.  The HyperDisplayFonts sketch provides
sizeable, rotatable characters to be used in HyperDisplay projects.  

Features:
  - 8-bit style characters
  - Rotate characters to 90, 180, or 270 degrees
  - Font sizes
      - 8x8   pixels (size 1)
      - 16x16 pixels (size 2)
      - 24x24 pixels (size 3)
      - 32x32 pixels (size 4)
      - 40x40 pixels (size 5)
      - 48x48 pixels (size 6)
      - 56x56 pixels (size 7)
      - 64x64 pixels (size 8)
      - ...up to 240x240 pixels (size 30)
  - Text positioning
      - x and y start position - provide the starting coordinates for the text string
      - center - x and y position is ignored and the text is centered on the screen
      - center with offsets - text is centered, but offset with x and y offsets

Function Reference:

  void aip_print_characters(char chars[], int startx, int starty, int factor, int rotate, int center, int coffx, int coffy, ILI9341_color_16_t txtcolor)
  
  Description: prints characters from the `chars` array to the screen
  
  Parameters:
      - chars[] - A character array of any size that will fit the screen, currently no line-wrap
      - startx - The start position on the screen for the x-axis
      - starty - The start position on the screen for the y-axis
      - factor - This is the font size, minimum value is 1
      - rotate - The degrees of rotation, accepted values 0, 90, 180, 270
      - center - If set to 1, text will be centered relative to offsets, xstart and ystart values are ignored
      - coffx  - Amount to offset x-axis from center, ignored when `center` is 0
      - coffy  - Amount to offset y-axis from center, ignored when `center` is 0
      - txtcolor - The color of the text in ILI9341_color_16_t format
      
      
  void aip_draw_character_bits(int idx, int x1, int y1, int factor, int rotate, ILI9341_color_16_t txtcolor)
  
  Description: prints a single character to the screen
  
  Parameters:
      - idx   - ASCII code (DEC number) for the character you want to draw to the screen
      - x1    - The starting x-position for the character
      - y1    - The starting y-position for the character
      - factor - The font size, minimum value 1
      - rotate - The degrees of rotation, accepted values 0, 90, 180, 270
      - txtcolor - The color of the text in ILI9341_color_16_t format
      
Known Issues:
  - Text positioning - text rotated to 180 or 270 degress is written to the screen in reverse order, the starting position is relative to the last printed character
  - Line-wrap - there is currently no support for line-wrapping, lines that are too long for the screen will overflow (text not visible)
  - Device support - Although this sketch should work for most HyperDisplay implementations, it has only been tested on the SparkFun `MicroMod Input and Display Carrier Board`
                     with 2.4" TFT display, 4DLCD-320240.
  - Time/Space complexity - CCP is not this developers primary language.  These functions have not been optimized for space and time.  The sketch was created for a hobby
                    project, not an enterprise application.
                    

Conclusion:
  Although it isn't perfect, it is hoped that this script may help another hobbiest implement fonts in their HyperDisplay project.
  
  apexNSW
