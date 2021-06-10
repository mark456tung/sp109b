multipass list 列出機器
multipass launch -n sp109b -c 4 -m 4G -d 40G
multipass shell sp109b
系統程式 9 4 5 1 3(這裡的組合語言比較類似 arm的)
asm 01 hack例子vm.c
虛擬機會模擬指令集 模擬器則可能只有表面而已
目前最常看到的虛擬機種類是寄生虛擬機(Hosted VM)
虛擬機分成三種架構 記憶體機 暫存器機 堆疊機(幾乎沒有cpu是這樣設計的)
Java的JVM虛擬機(堆疊機)
02 pitifulvm
QEMU可以在RISC-V上跑 ARM X86 反之亦然 速度大約只比原生慢兩到三倍
稍微介紹c4(可以自我編譯)有內建堆疊虛擬機