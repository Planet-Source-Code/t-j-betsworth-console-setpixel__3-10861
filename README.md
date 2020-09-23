<div align="center">

## Console SetPixel


</div>

### Description

using SetPixel function with

the gdi link for graphical use

in a console window.
 
### More Info
 
Requires win32 console project.

Requires libgdi32.a

Add libgdi32.a to linker via

project options/parameters/linker.


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[T J Betsworth](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/t-j-betsworth.md)
**Level**          |Intermediate
**User Rating**    |4.7 (14 globes from 3 users)
**Compatibility**  |C\+\+ \(general\)
**Category**       |[Graphics/ Sound](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/graphics-sound__3-15.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/t-j-betsworth-console-setpixel__3-10861/archive/master.zip)





### Source Code

```
#include <iostream>
#include <stdlib.h>
#include <windows.h>
#include <math.h>
using namespace std;
int main(){
  int i,x,y;
  SetConsoleTitle("Console SetPixel");
  HANDLE hout = GetStdHandle(STD_OUTPUT_HANDLE);
  COORD coord = {95, 40};
  SMALL_RECT rec = {0,0,0,0};
  SetConsoleScreenBufferSize(hout, coord);
  rec.Right = coord.X -1;
  rec.Bottom = coord.Y -1;
  SetConsoleWindowInfo(hout,TRUE,&rec);
  CONSOLE_CURSOR_INFO cci;
  cci.dwSize = 25;
  cci.bVisible = FALSE;
  SetConsoleCursorInfo(hout, &cci);
  COORD coord1; coord1.X = 0; coord1.Y= 0; DWORD wr;
  FillConsoleOutputAttribute( hout,255,95*40,coord1,&wr);
  HWND hWnd = FindWindow(NULL, "Console SetPixel");
  HDC hdc = GetDC(hWnd);
  for(i = 0;i <9000;i++){
    x=rand () %480; y=rand ()%480;
    SetPixel(hdc, x, y, RGB(rand() % 255, rand() % 255, rand() % 255));
  }
  for(i = 0;i <1257;i++){
        x=(int)(200* cos(6.28*i/1257)+240);
        y=(int)(200* sin(6.28*i/1257)+240);
        SetPixel(hdc, x, y, RGB( 255,0,0));
   }
  for(x = 0; x < 760; x+=3){
    y = 240;
    SetPixel(hdc, x, y, RGB(255,0,0));
  }
  for(y = 0; y < 480; y+=3){
    x = 240;
    SetPixel(hdc, x, y, RGB(255,0,0));
  }
  for(x = 44; x < 437; x++){
    y = (int)(76.4*sin(x/76.4) * cos(x/76.4) + 240);
    SetPixel(hdc, x, y, RGB(0,0,255));
  }
  for(y = 44; y < 437; y++){
    x = (int)(75.8*sin(y/75.8) * cos(y/75.8) + 240);
    SetPixel(hdc, x, y, RGB(0,0,255));
  }
       HFONT font;
       font = CreateFont(30, 0, 90, 0, 0, TRUE,0,0,0,0,0,0,0,"Dotum");
       SelectObject(hdc, font);
       SetBkColor(hdc,RGB(255,255,255));
       SetTextColor(hdc, RGB(0, 0, 255));
       TextOut(hdc, 555,100, "Console", 7);
       TextOut(hdc, 557,140, "SetPixel", 8);
       DeleteObject(font);
       ReleaseDC(hWnd, hdc);
       DeleteDC(hdc);
  COORD coord2 = {62, 29};
  SetConsoleCursorPosition(hout, coord2);
  SetConsoleTextAttribute(hout,249);
  system("PAUSE");
  return 0;
  }
```

