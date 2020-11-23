# Danghui-LVM
Danghui is a Roblox CLVM (very hard to patch) that uses a relatively brand new script execution method to execute arbitrary code on Roblox's own main lua_State. Since 2017, this project has been depreciated due to Roblox's implementation of memory checking.

CLVM's objective is to achieve script execution through a custom virtual machine that operates on a foreign, untranslated and incompatable lua state. It copies the Lua C functions from Roblox to a seperate DLL, and does so *WITHOUT BYPASSING ANY MAJOR CHECKS. (memcheck, retcheck, hookcheck, etc)*. 


- Able to index every class
- Able to set any property
- Calling all Roblox functions
- Accessing all Roblox global tables
- Context level 7, acecess to CoreGUI, ScriptContext, etc.
- NO YIELDING, NO HTTP/LOADSTRING SUPPORT.

Issues:
- Lua functions like lua_resume and lua_yield will not work as expected, as the VM is tasked with handling the yield. Since we execute code locally on the CLVM, yields act differently.
- Checks such as the simple "hackflag" check in lua C functions need to be bypassed manually, then quickly reverted in a short period of time in order to prevent the memory checker from flagging any modifications in memory. 

![alt text](https://i.gyazo.com/ce3605f365825afa4b608ebfd360bcbf.png)
