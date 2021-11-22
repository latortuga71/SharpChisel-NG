# SharpChisel-NG

# What is this ?
Custom chisel version that is embedded in c# automatically built with azure devops, so when a new chisel version releases. The Release page should update with a new version. And hopefully it keeps working with donut and load assembly.

# Why ?
![SharpChisel](https://github.com/shantanu561993/SharpChisel) Wasnt working with donut, also it wasnt working with load assembly.
Also on its own it wasnt working with the latest version of regular chisel. So i needed to get it working and decided to automate it.

# How do i use this?
Download the exe, and provide the command line args as you normally would.
Also if you use donut you need to pass the cmdline args when creating the shellcode.
To look at help menu use regular chisel.

# Code
```csharp
using System.Runtime.InteropServices;
using System.Text;

namespace SharpChisel_NG
{
    public class Program
    {
        [DllImport("chisel", EntryPoint = "RunMe")]
        public extern static void RunMe(byte[] test);
        public static void Main(string[] args)
        {
            var strArgs = string.Join(" ", args);
            RunMe(Encoding.ASCII.GetBytes(strArgs));
        }
    }
}
```



# Credits
* https://medium.com/@shantanukhande/red-team-how-to-embed-golang-tools-in-c-e269bf33876a
* https://github.com/shantanu561993/SharpChisel
* https://github.com/jpillora/chisel
