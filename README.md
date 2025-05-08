# Chams BO2 XeX Code


Address.h :
```cpp
addrs.BodyChams = 0x821FC04C;
```

Visuals.cpp :
```cpp
void Visuals::UpdateChams() {
	if (MenuOptions::bDrawChams) {
		BYTE patch[] = { 0x38, 0xC0, 0xFF, 0xFF };
		memcpy((void*)decryptDWORD(Security->addrs.BodyChams), patch, sizeof(patch));
	}
	else {
		BYTE patch[] = { 0x7F, 0xA6, 0xEB, 0x78 };
		memcpy((void*)decryptDWORD(Security->addrs.BodyChams), patch, sizeof(patch));
	}
}


// PLACE INSIDE  Visuals::HandleVisuals() FUNCTION
if ((MenuOptions::bDrawAllies && !bIsEnemy) || (MenuOptions::bDrawAxis && bIsEnemy) && MenuOptions::bDrawChams ) {
	Visuals::UpdateChams();
}


```

Menu.cpp :
```cpp
	Menu("Draw Chams").Toggle(&MenuOptions::bDrawChams);
```

Globals.h :
```cpp
extern BOOL bDrawChams;
```

Globals.cpp :
```cpp
BOOL MenuOptions::bDrawChams = FALSE;
```
 Based off of Sunset / Darling v1.1, Credits to them for the menu

