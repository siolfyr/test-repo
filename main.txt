#include <Windows.h>
#include <iostream>

void drawRect(RECT rct)
{
    HDC hdc = ::GetDC(0);

    HBRUSH blueBrush=CreateSolidBrush(RGB(0,0,255));
    FillRect(hdc, &rct, blueBrush);

    ReleaseDC(0, hdc);
}
int main(void)
{
    char c;

    RECT rct;
    rct.left=10;
    rct.right=100;
    rct.top=10;
    rct.bottom=200;

    while(1)
    {
        std::cin >> c;
        if (c == 'd') drawRect(rct);
        else if(c == 'e')
        {
            InvalidateRect(NULL, NULL, TRUE);
        }
    }
    return 0;
}
