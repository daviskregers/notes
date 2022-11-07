# Installation

We can follow the guide on [https://kubernetes.io/docs/tasks/tools/install-minikube/](https://kubernetes.io/docs/tasks/tools/install-minikube/) .

# Before you begin

Check required vmx / svm support.

```
davis@davis-arch  /tmp  egrep --color 'vmx|svm' /proc/cpuinfo
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm cpuid_fault epb pti tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt dtherm ida arat pln pts
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm cpuid_fault epb pti tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt dtherm ida arat pln pts
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm cpuid_fault epb pti tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt dtherm ida arat pln pts
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm cpuid_fault epb pti tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt dtherm ida arat pln pts
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm cpuid_fault epb pti tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt dtherm ida arat pln pts
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm cpuid_fault epb pti tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt dtherm ida arat pln pts
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm cpuid_fault epb pti tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt dtherm ida arat pln pts
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm cpuid_fault epb pti tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt dtherm ida arat pln pts
```

## Install a Hypervisor

```
sudo pacman -Syu
```

```
 davis@davis-arch  /tmp  sudo pacman -S virtualbox
resolving dependencies...
:: There are 2 providers available for VIRTUALBOX-HOST-MODULES:
:: Repository community
   1) virtualbox-host-dkms  2) virtualbox-host-modules-arch

Enter a number (default=1): 2
looking for conflicting packages...

Packages (4) qt5-x11extras-5.12.1-1  sdl-1.2.15-10  virtualbox-host-modules-arch-6.0.4-12  virtualbox-6.0.4-4

Total Download Size:    62.05 MiB
Total Installed Size:  178.07 MiB

:: Proceed with installation? [Y/n] 
:: Retrieving packages...
 sdl-1.2.15-10-x86_64                          341.3 KiB  1219K/s 00:00 [########################################] 100%
 qt5-x11extras-5.12.1-1-x86_64                  13.0 KiB  4.24M/s 00:00 [########################################] 100%
 virtualbox-host-modules-arch-6.0.4-12-x86_64  162.0 KiB  1742K/s 00:00 [########################################] 100%
 virtualbox-6.0.4-4-x86_64                      61.6 MiB  1402K/s 00:45 [########################################] 100%
(4/4) checking keys in keyring                                          [########################################] 100%
(4/4) checking package integrity                                        [########################################] 100%
(4/4) loading package files                                             [########################################] 100%
(4/4) checking for file conflicts                                       [########################################] 100%
(4/4) checking available disk space                                     [########################################] 100%
:: Processing package changes...
(1/4) installing sdl                                                    [########################################] 100%
Optional dependencies for sdl
    alsa-lib: ALSA audio driver [installed]
    libpulse: PulseAudio audio driver [installed]
(2/4) installing qt5-x11extras                                          [########################################] 100%
(3/4) installing virtualbox-host-modules-arch                           [########################################] 100%
(4/4) installing virtualbox                                             [########################################] 100%
Optional dependencies for virtualbox
    vde2: Virtual Distributed Ethernet support
    virtualbox-guest-iso: Guest Additions CD image
    virtualbox-ext-vnc: VNC server support
    virtualbox-sdk: Developer kit
:: Running post-transaction hooks...
(1/8) Updating linux module dependencies...
(2/8) Updating icon theme caches...
(3/8) Reloading system manager configuration...
(4/8) Creating system user accounts...
(5/8) Reloading device manager configuration...
(6/8) Arming ConditionNeedsUpdate...
(7/8) Updating the desktop file MIME type cache...
(8/8) Updating the MIME type database...
```

```
 davis@davis-arch  /tmp  virtualbox
WARNING: The vboxdrv kernel module is not loaded. Either there is no module
         available for the current kernel (5.0.0-arch1-1-ARCH) or it failed to
         load. Please recompile the kernel module and install it by

           sudo /sbin/vboxconfig

         You will not be able to start VMs until this problem is fixed.
 davis@davis-arch  /tmp  sudo modprobe vboxdrv
 davis@davis-arch  /tmp  virtualbox
 davis@davis-arch  /tmp  
```

## Install kubectl

```
davis@davis-arch  /tmp  curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.13.4/bin/linux/amd64/kubectl

  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 37.4M  100 37.4M    0     0  1662k      0  0:00:23  0:00:23 --:--:-- 1634k
 davis@davis-arch  /tmp  chmod +x ./kubectl

davis@davis-arch  /tmp  sudo mv ./kubectl /usr/local/bin/kubectl
davis@davis-arch  /tmp  kubectl version
Client Version: version.Info{Major:"1", Minor:"13", GitVersion:"v1.13.4", GitCommit:"c27b913fddd1a6c480c229191a087698aa92f0b1", GitTreeState:"clean", BuildDate:"2019-02-28T13:37:52Z", GoVersion:"go1.11.5", Compiler:"gc", Platform:"linux/amd64"}
The connection to the server localhost:8080 was refused - did you specify the right host or port?
```

## Install minikube

```
davis@davis-arch  /tmp  curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 \
  && chmod +x minikube
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 38.2M  100 38.2M    0     0  1714k      0  0:00:22  0:00:22 --:--:-- 1523k
 davis@davis-arch  /tmp  sudo cp minikube /usr/local/bin && rm minikube

 davis@davis-arch  /tmp  minikube version
minikube version: v0.35.0
```

## Start minikube

```
davis@davis-arch  ~  minikube start 
o   minikube v0.35.0 on linux (amd64)
>   Creating virtualbox VM (CPUs=2, Memory=2048MB, Disk=20000MB) ...
-   "minikube" IP address is 192.168.99.101
-   Configuring Docker as the container runtime ...
-   Preparing Kubernetes environment ...
-   Pulling images required by Kubernetes v1.13.4 ...
-   Launching Kubernetes v1.13.4 using kubeadm ... 
:   Waiting for pods: apiserver proxy etcd scheduler controller addon-manager dns
-   Configuring cluster permissions ...
-   Verifying component health .....
+   kubectl is now configured to use "minikube"
=   Done! Thank you for using minikube!

```

```
davis@davis-arch  ~  minikube status
host: Running
kubelet: Running
apiserver: Running
kubectl: Correctly Configured: pointing to minikube-vm at 192.168.99.101
```

```
davis@davis-arch  ~  kubectl cluster-info
Kubernetes master is running at https://192.168.99.101:8443
KubeDNS is running at https://192.168.99.101:8443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.

```
