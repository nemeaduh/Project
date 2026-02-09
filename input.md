<img src="./u44vrz51.png" style="width:7.5in;height:2.62917in" /><img src="./oibh11ft.png" style="width:7.5in;height:0.95833in" />

> **ASSIGNMENT** **IV** **Microsoft** **Azure** **Administrator**
>
> **Neme** **Aduh**

**How** **to** **Add** **a** **Data** **Disk** **to** **a** **Rocky**
**LinuxVM** **using** **after** **the** **VM** **has** **been**
**deployed**

> • **Create** **a** **Rocky** **LVM** **and** **deploy**
>
> • **Goto** **the** **VM** **deployed\>** **click** **on**
> **settings\>Disk**
>
> • **Under** **Data** **disks** **-** **Click** **‘Create** **and**
> **attach** **a** **new** **disk’**
>
> • **Define** **the** **Disk** **name,** **storage** **tyoe,** **size**
> **etc** **then** **hit** **‘Apply’** **to** **deploy** **the**
> **newly** **created** **disk**

**Next** **Step** **is** **to** **connect** **to** **the** **VM**
**using** **MobaXterm** **and** **Initialize** **the** **Disk**

> • **Connect** **to** **the** **LVM** **using** **MobaXterm**
>
> •  **For** **me** **to** **become** **the** **root** **user** **that**
> **is** **the** **super** **user** **to** **be** **able** **to**
> **run** **admin** **commands** **without** **using** **sudo,** **I**
> **used** **the** **command** **‘sudo** **passwd** **root’** **to**
> **change** **the** **password** **then** **I** **switch** **user**
> **by** **running** **command** **‘su** **–‘**

<img src="./iadqa4uq.png"
style="width:7.49931in;height:2.52153in" /><img src="./gejh0ihw.png"
style="width:5.28125in;height:1.82292in" />

> • **To** **show** **the** **Disk** **usage,** **run** **a**
> **command** **‘df** **-h’** • **Sda2** **is** **the** **OS** **disk**
>
> • **Sdb1** **is** **the** **Temporary** **disk**
>
> • **So** **we** **currently** **do** **not** **have** **the** **Data**
> **disk** **showing** **yet**
>
> <img src="./4lj3nka5.png"
> style="width:6.99792in;height:3.45194in" />• **But,** **typing**
> **the** **command** **‘fdisk** **-l’** **shows** **the** **Data**
> **Disk** **which** **is** **sdc** **but** **it** **has** **not**
> **been** **partition**

• **Since** **the** **name** **of** **the** **DataDisk** **as** **seen**
**is** **‘dev/sdc/** **,** **we** **will** **now** **go** **into**
**the** **disk** **using** **command** **‘fdisk** **/dev/sdc/**

• **Type** **m** **for** **help**

<img src="./30nik5yh.png"
style="width:6.34431in;height:7.84444in" />• **So** **we** **want**
**to** **type** **‘n’** **to** **add** **a** **new** **partition**

> • **In** **this** **first** **partition,** **we** **have** **created**
> **20GB** **out** **of** **the** **64GB**
> **Data**<img src="./rzzh25eh.png"
> style="width:7.34375in;height:2.03125in" /><img src="./q35ygtee.png"
> style="width:6.28125in;height:2.58333in" />

• **To** **save** **this** **partition,** **run** **‘w’** **and**
**enter,** **The** **partition** **table** **been** **altered**
**means** **is** **now** **saved**

• **Next** **Step,** **In** **as** **much** **this** **sdc** **has**
**been** **partitioned,** **if** **you** **run** **a** **command**
**‘df** **-h’** **you** **won’t** **still** **see** **it** **which**
**means** **it** **is** **yet** **to** **be** **‘cooked’**

<img src="./gxfopcct.png"
style="width:6.74792in;height:3.27778in" />• **So** **to** **cook**
**this** **we** **run** **a** **command** **‘mkfs.xfs** **/dev/sdc1**

> • **In** **as** **much** **as** **this** **has** **been** **cooked,**
> **we** **still** **need** **to** **mount** **the** **partition**
> **data** **disk** **for** **it** **to** **display** • **So** **we**
> **are** **going** **to** **make** **a** **directory** **where** **we**
> **want** **to** **mount** **the** **data** **disk** **by** **running**
> **the**<img src="./535st4yb.png"
> style="width:4.29167in;height:0.59375in" /><img src="./2gzsumlc.png"
> style="width:5.21875in;height:2.27083in" /><img src="./f1x3txuo.png" style="width:7.5in;height:2.75278in" />
>
> **command** **‘mkdir** **/nemeData’**
>
> • **Once** **a** **directory** **has** **been** **made,** **we**
> **can** **then** **run** **the** **command** **‘mount** **/dev/sdc1**
> **/nemeData/**
>
> • **To** **confirm** **the** **mount** **has** **been** **done,**
> **run** **‘df** **-h’**
>
> • **But** **this** **mount** **has** **not** **been** **saved**
> **permanently,** **so** **to** **do** **this,** **we** **run** **the**
> **command** **‘echo** **“/dev/sdc1** **/nemeData** **xfs**
> **defaults** **0** **0”** **\>\>** **/etc/fstab**
>
> • **To** **confirm** **this** **is** **now** **mounted** **by**
> **default/permanently,** **run** **the** **command** **‘cat**
> **/etc/fstab’**

**Validation** **check:/dev/sdc1** **/nemeData** **xfs** **defaults**
**0** **0’** **displays** **which** **shows** **this** **is** **now**
**mounted** **by** **defaulted** **into** **fstab**

**We** **can** **unmount** **using** **command** **‘umount**
**/nemeData’**

**We** **can** **mount** **it** **back** **using** **the** **command**
**‘mount** **-a’**
