<div align="center">

## How To MAKE a window, NO MFC


</div>

### Description

Well, want to ACTUALLY create your own form? no MFC or Resources. This is code to actually make a raw form. easy to use. Please gimme feed back.
 
### More Info
 
copy and paste the code

since no one really gives good explinations. heres one:

1. open visual c++

2. File > New

3. Click Projects tab

4. click Win32 Application and give it a name

5. click finish

6. click the File View Tab on TreeView

7. go to File > New

8. in the first tab Click C++ Source File and name it

9. Copy and paste the code in the new file

10. right click the Header folder and add Windows.h

11. click execute

12. give me feedback and vote -=]

a window

none at all


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Mehdi Hanbali](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/mehdi-hanbali.md)
**Level**          |Beginner
**User Rating**    |4.5 (95 globes from 21 users)
**Compatibility**  |Microsoft Visual C\+\+
**Category**       |[Controls/ Forms/ Dialogs/ Menus](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/controls-forms-dialogs-menus__3-3.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/mehdi-hanbali-how-to-make-a-window-no-mfc__3-686/archive/master.zip)

### API Declarations

you need to include windows.h, it comes with visual c++


### Source Code

```
#include <windows.h>
LRESULT CALLBACK WindowFunc(HWND, UINT, WPARAM, LPARAM);
char szWinNamw[] = "MyWin";
int WINAPI WinMain(HINSTANCE hThisInst, HINSTANCE hPrevInst,
				  LPSTR kposzArgs, int nWinMode)
{
	HWND hwnd;
	MSG msg;
	WNDCLASSEX wcl;
	wcl.cbSize = sizeof(WNDCLASSEX);
	wcl.hInstance = hThisInst;
	wcl.lpszClassName = "My Window";
	wcl.lpfnWndProc = WindowFunc;
	wcl.style = 0;
	wcl.hIcon = LoadIcon(NULL, IDI_APPLICATION);
	wcl.hIconSm = LoadIcon(NULL, IDI_WINLOGO);
	wcl.hCursor = LoadCursor(NULL, IDC_ARROW);
	wcl.lpszMenuName = NULL;
	wcl.cbClsExtra = 0;
	wcl.cbWndExtra = 0;
	wcl.hbrBackground = (HBRUSH) GetStockObject(WHITE_BRUSH);
	if(!RegisterClassEx(&wcl)) return 0;
	hwnd = CreateWindow(
		"My Window",
		"Skeleton Window",
		WS_OVERLAPPEDWINDOW,
		CW_USEDEFAULT,
		CW_USEDEFAULT,
		CW_USEDEFAULT,
		CW_USEDEFAULT,
		HWND_DESKTOP,
		NULL,
		hThisInst,
		NULL
		);
	ShowWindow(hwnd, nWinMode);
	UpdateWindow(hwnd);
	while(GetMessage(&msg, NULL, 0, 0))
	{
		TranslateMessage(&msg);
		DispatchMessage(&msg);
	}
	return msg.wParam;
}
LRESULT CALLBACK WindowFunc(HWND hwnd, UINT message,
							WPARAM wParam, LPARAM lParam)
{
	switch(message)	{
	case WM_DESTROY:
		PostQuitMessage(0);
		break;
	default:
		return DefWindowProc(hwnd, message, wParam, lParam);
	}
	return 0;
}
```

