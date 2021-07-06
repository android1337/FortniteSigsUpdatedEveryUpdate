# FortniteSigsUpdatedEveryUpdate
Fortnite Signatures / Patterns updated every update
Ez Fortnite Sigs for your pasta

Updated season 7  latest update
The rise of Internals, The rise of Pasters only 4u.
Credits to https://github.com/homeless1337 for GetObjectName Function
```cpp

Uworld: 48 8B 05 ? ? ? ? 4D 8B C2
GoObject: 48 8B 05 ? ? ? ? 48 8B 0C C8 48 8B 04 D1
FnFree: 48 85 C9 0F 84 ? ? ? ? 53 48 83 EC 20 48 89 7C 24 30 48 8B D9 48 8B 3D ? ? ? ? 48 85 FF 0F 84 ? ? ? ? 48 8B 07 4C 8B 40 30 48 8D 05 ? ? ? ? 4C 3B C0
ProjectWorldToScreen: E8 ? ? ? ? 41 88 07 48 83 C4 30
GetBoneMatrix: E8 ? ? ? ? 48 8B 47 30 F3 0F 10 45
LineOfSightTo: E8 ? ? ? ? 48 8B 0D ? ? ? ? 33 D2 40 8A F8
CalculateSpreadHook = E8 ? ? ? ? 48 8D 4B 28 E8 ? ? ? ? 48 8B C8
SpreadCaller = 0F 57 D2 48 8D 4C 24 ? 41 0F 28 CC E8 ? ? ? ? 48 8B 4D B0 0F 28 F0 48 85 C9
GetNameByIndex = 48 89 5C 24 ? 48 89 74 24 ? 55 57 41 56 48 8D AC 24 ? ? ? ? 48 81 EC ? ? ? ? 48 8B 05 ? ? ? ? 48 33 C4 48 89 85 ? ? ? ? 45 33 F6 48 8B F2 44 39 71 04 0F 85 ? ? ? ? 8B 19 0F B7 FB E8 ? ? ? ? 8B CB 48 8D 54 24
GetObjectName: instead of this sig use the function below


std::string GetObjectName(uintptr_t Object) {
 
            static uintptr_t addr = 0;
 
            if (!addr) {
                addr = FindPattern(xorstr(GetNameByIndexSignature); //GetNameByIndex sig
                if (!addr) {
                    MessageBoxA((HWND)0, (LPCSTR)_("Failed to get GetNameByIndex"), (LPCSTR)0, (UINT)0);
                    exit(0);
                }
            }
 
            if (Object == NULL)
                return _("");
 
            auto fGetObjName = reinterpret_cast<FString * (__fastcall*)(int* index, FString* res)>(addr);
 
            int index = *(int*)(Object + 0x18);
 
            FString result;
            fGetObjName(&index, &result);
 
            if (result.c_str() == NULL)
                return _("");
 
            auto result_str = result.ToString();
 
            if (result.c_str() != NULL)
                Free((__int64)result.c_str());
 
            return result_str;
        }



```

If you don't know how to update your pasta cause maybe it accept only pattetns and not sigs just change the ? with a 00 and before every part add \x example:

Before -> ```cpp 48 8B 0D ? ? ? ? 48 98```
After ->  ```cpp \x48\x8B\x0D\x00\x00\x00\x00\x48\x98```


If you have any troubles dm me on discord: android#1337

