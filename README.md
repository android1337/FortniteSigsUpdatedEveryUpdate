# FortniteSigsUpdatedEveryUpdate
Fortnite Signatures / Patterns updated every update
Ez Fortnite Sigs for your pasta

Updated season 6
The rise of Internals, The rise of Pasters only 4u.
```cpp

GoObject: 48 8B 05 ? ? ? ? 48 8B 0C C8 48 8B 04 D1
FnFree: 48 85 C9 0F 84 ? ? ? ? 53 48 83 EC 20 48 89 7C 24 30 48 8B D9 48 8B 3D ? ? ? ? 48 85 FF 0F 84 ? ? ? ? 48 8B 07 4C 8B 40 30 48 8D 05 ? ? ? ? 4C 3B C0
Uworld: 48 8B 05 ? ? ? ? 4D 8B C2
ProjectionMatrixGivenView: E8 ? ? ? ? 41 88 07 48 83 C4 30
FNamePool: 48 8B 1D ? ? ? ? 48 03 C0
GetBoneMatrix: E8 ? ? ? ? F3 0F 10 48 38
LineOfSightTo: E8 ? ? ? ? 48 8B 0D ? ? ? ? 33 D2 40 8A F8
GetObjectName: instead of this sig use the function below


std::string GetObjectName(uintptr_t Object) {
 
            static uintptr_t addr = 0;
 
            if (!addr) {
                addr = FindPattern(xorstr("\x48\x89\x5C\x24\x00\x48\x89\x74\x24\x00\x55\x57\x41\x56\x48\x8D\xAC\x24\x00\x00\x00\x00\x48\x81\xEC\x00\x00\x00\x00\x48\x8B\x05\x00\x00\x00\x00\x48\x33\xC4\x48\x89\x85\x00\x00\x00\x00\x45\x33\xF6\x48\x8B\xF2\x44\x39\x71\x04\x0F\x85\x00\x00\x00\x00\x8B\x19\x0F\xB7\xFB\xE8\x00\x00\x00\x00\x8B\xCB\x48\x8D\x54\x24"), xorstr("xxxx?xxxx?xxxxxxxx????xxx????xxx????xxxxxx????xxxxxxxxxxxx???xxxxxx????xxxxxx"); //GetNameByIndex sig
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


If you have any troubles dm me on discord: Android#1336
