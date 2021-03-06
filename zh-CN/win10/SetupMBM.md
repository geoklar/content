 <h3> 所需内容 </h3>
    运行 Windows 10 的电脑（在上一步中已准备就绪）。<br>
    MinnowBoard MAX<br>
    电源，至少 1.0A 电流。 如果计划使用多个高耗电 USB 外设，请改用电流较高的电源 (>2.0A)。<br>
    8GB 微型 SD 卡 - 类 10 或更高。我们建议使用<a href="http://www.amazon.com/gp/product/B00IVPU786" target="_blank">这个</a>或<a href="http://www.amazon.com/SanDisk-Ultra-Micro-SDHC-16GB/dp/9966573445" target="_blank">这个</a>。<br>
    HDMI 电缆和监视器<br>
    以太网电缆<br>
    USB 键盘
    微型 SD 卡读卡器 - 因为大多数内部微型 SD 卡读卡器均会出现问题，所以我们建议使用外部 USB 微型 SD 卡读卡器，例如<a href="http://www.amazon.com/Transcend-Information-Card-Reader-TS-RDF5K/dp/B009D79VH4" target="_blank">这个</a>或<a href="http://www.amazon.com/Kingston-Digital-MobileLite-Multi-Function-FCR-MLG4/dp/B00KX4TORI" target="_blank">这个</a><br>
  <h3> 连接开发板</h3>
  <ol class="setup-content-list">
    <div class="row">
      <div class="col-md-6 col-sm-12">
          <li><b>将 USB 键盘连接</b>到开发板上的 USB 端口之一。</li>
          <li><b>将 HDMI 监视器连接</b>到开发板上的 microHDMI 端口。</li>
          <li>
            <b>将网络电缆连接</b>到开发板上的以太网端口。请确保开发电脑在同一网络上。
            <ul>
              <li><b>注意：</b> 如果没有本地有线网络，请参阅<a href="{{site.baseurl}}/{{page.lang}}/win10/ConnectToDevice.htm" target="_blank">此处</a>获取其他连接选项。</li>
            </ul>
          </li>
      </div>
      <div class="col-md-6 col-sm-12">
        <img src="{{site.baseurl}}/Resources/images/mbm.bmp" class="device-images">
      </div>
    </div>
  </ol>
<h3>更新设备固件</h3>
    <ol class="setup-content-list">
      <div class="row">
        <div class="col-sm-12">
          <li>对于当前版本，仅支持 32 位 Windows 10 IoT 核心版。 从 <a href="http://firmware.intel.com/projects/minnowboard-max" target="_blank">firmware.intel.com/projects/minnowboard-max</a> 下载最新版本的 32 位预生成的 BIOS 固件</li>
          <li>
            解压缩已下载的文件并将以下文件复制到 FAT 格式化的 U 盘
            <ul>
              <li>*.efi</li>
              <li>*.bin</li>
            </ul>
          </li>
          <li>关闭 MinnowBoard 电源</li>
          <li>删除任何 SD 卡和外部硬盘驱动器</li>
          <li>将 U 盘插入 MinnowBoard</li>
          <li>打开 MinnowBoard 电源</li>
          <li>
            应看到 UEFI 提示。在 UEFI 提示下运行以下命令：
          </li>
          <li>
            <p>如果当前固件是 64 位（这是 MinnowBoard 的原始状态）</p>
              <kbd>fs0：</kbd>
              <kbd>.\MinnowBoard.MAX.FirmwareUpdateX64.efi _filename_.bin</kbd>
            <p> 如果当前固件是 32 位（如果你已将原始固件修改为 32 位） </p>
              <kbd>fs0：</kbd>
              <kbd>.\MinnowBoard.MAX.FirmwareUpdateIA32.efi _filename_.bin</kbd>
            <p> 例如</p>
              <kbd>Shell> fs0：</kbd>
              <kbd>fs0:\> .\MinnowBoard.MAX.FirmwareUpdateIA32.efi MinnowBoard.MAX.I32.079.R01.bin</kbd>
          </li>
          <li>
            系统应在固件更新完成后自动关闭。
            <ul>
              <li> 注意： 如果你无法转到 fs0: 分区，请尝试使用不同的闪存驱动器。即使在你复制了 efi/bin 文件后，某些闪存驱动器仍无法启动。</li>
            </ul>
          </li>
        </div>
      </div>
    </ol>
    <p> 你可能想知道为什么需要调用“MinnowBoard.MAX.FirmwareUpdateX64.efi”，即使我们仅支持 32 位版本的 Windows 10 IoT 核心版。
        该板通常随附已预安装在其上的 64 位固件。 EFI 的位数必须与当前固件的位数匹配。 另外，bin 文件的位数还必须与更新该固件所需的位数匹配。
        因此，首次更新时你可能会需要使用 64 位 EFI 和 32 位 BIN。
        第二次更新以及其他任意一次更新时你需要使用 32 位 EFI 和 32 位 BIN。
        固件的位数必须与操作系统的位数匹配的原因是，在启动操作系统时加载的操作系统映像中存在一个 EFI，该 EFI 的位数也必须与固件的位数相同。</p>
<h3> 安装 Windows 10 IoT 核心版工具 </h3>
  <ol class="setup-content-list">
    <div class="row">
      <div class="col-md-6 col-sm-12">
        <li>
          从我们的<a href="{{site.baseurl}}/{{page.lang}}/Downloads.htm" target="_blank">下载页</a>下载 Windows 10 IoT 核心版映像。将 ISO 保存到本地文件夹。
        </li>
      </div>
      <div class="col-md-6 col-sm-12">
        <img class="image-border" src="{{site.baseurl}}/Resources/images/mbm_iso.png">
      </div>
    </div>
    <div class="row">
      <div class="col-md-6 col-sm-12">
        <li>
          双击 ISO (IoT Core MBM.iso) 会自动将其作为虚拟 CD 驱动器进行装载，以便你可以访问内容。
        </li>
      </div>
      <div class="col-md-6 col-sm-12">
        <img class="image-border" src="{{site.baseurl}}/Resources/images/mbm_msi.PNG">
      </div>
    </div>
    <div class="row">
      <div class="col-md-6 col-sm-12">
        <li>
          安装 <b>Windows_10_IoT_Core_Mbm.msi</b>。安装完成后，flash.ffu 将位于 <b>C:\Program Files (x86)\Microsoft IoT\FFU\MinnowBoardMax</b> 上。
        </li>
      </div>
      <div class="col-md-6 col-sm-12">
        <img class="image-border" src="{{site.baseurl}}/Resources/images/mbmffu.PNG">
      </div>
    </div>
    <div class="row">
      <div class="col-md-6 col-sm-12">
        <li>
          安装完成后，弹出虚拟 CD - 可通过以下步骤完成此操作：导航到文件资源管理器的顶级文件夹、右键单击该虚拟驱动器，然后选择“弹出”。
        </li>
      </div>
    </div>
  </ol>
<h3> 将 Windows 10 IoT 核心版映像放置在 SD 卡上 </h3>
  <ol class="setup-content-list">
    <div class="row">
      <div class="col-md-6 col-sm-12">
        <li>
          将微型 SD 卡插入 SD 卡读卡器。
        </li>
      </div>
      <div class="col-md-6 col-sm-12">
      </div>
    </div>
    <div class="row">
      <div class="col-md-6 col-sm-12">
        <li>
           使用 IoTCoreImageHelper.exe 刷写 SD 卡。从“开始”菜单搜索“WindowsIoT”，并选择快捷方式“WindowsIoTImageHelper”。
        </li>
      </div>
      <div class="col-md-6 col-sm-12">
        <img src="{{site.baseurl}}/Resources/images/ImagerHelperSearch.PNG">
      </div>
    </div>
    <div class="row">
      <div class="col-md-6 col-sm-12">
        <li>
          <p>该工具将枚举设备，如下所示。选择你希望刷写的 SD 卡，然后提供 FFU 的位置以刷入映像。</p>
          <p><b>注意：</b> IoTCoreImageHelper.exe 是推荐用来刷写 SD 卡的工具。但是，说明可用于直接使用 <a href="{{site.baseurl}}/{{page.lang}}/win10/samples/DISM.htm" target="_blank">DISM 命令行工具</a>。</p>
        </li>
      </div>
      <div class="col-md-6 col-sm-12">
        <img src="{{site.baseurl}}/Resources/images/mbm_imagehelper.PNG">
      </div>
    </div>
    <div class="row">
      <div class="col-md-6 col-sm-12">
        <li>
          <p>通过以下步骤可安全删除你的 USB SD 卡读卡器：单击任务栏中的“安全删除硬件”，或在文件资源管理器中找到 USB 设备，然后右键单击并选择“弹出”。 如果未正确执行此操作，可能导致映像损坏。</p>
          <p><b>注意：</b> 如果你希望在使用完 Windows 10 IoT 核心版后将其从 SD 卡中删除，请参阅标题为“如何从我的 SD 卡中删除 Windows 10 IoT 核心版？”的<a href="{{site.baseurl}}/{{page.lang}}/Faqs.htm" target="_blank">常见问题</a>部分。</p>
        </li>
      </div>
      <div class="col-md-6 col-sm-12">
      </div>
    </div>
  </ol>

<h3>设置所需的 BIOS 设置并启动 Windows 10 IoT 核心版</h3>
<ol class="setup-content-list">
  <div class="row">
    <div class="col-md-6 col-sm-12">
      <li>将微型 SD 卡插入 MBM 中。 无论在何时打开 MBM，只要其中未插入 SD 卡，系统都将要求重新配置启动顺序。</li>
      <li>启动后，按 F2 访问 BIOS 设置。</li>
      <li>
        依次导航到“设备管理器”->“系统设置”->“南群集配置”->“LPSS 和 SCC 配置”
        <ul>
          <li>将“LPSS PWM #1 支持”设置为“禁用”</li>
          <li>将“LPSS PWM #2 支持”设置为“禁用”</li>
        </ul>
      </li>
      <li>导航回顶层并依次选择“启动维护管理器”->“启动选项”>“更改启动顺序”</li>
      <li>突出显示启动顺序列表（突出显示时，将在屏幕右侧看到“更改顺序”），然后按 Enter 键</li>
      <li>突出显示“EFI 杂项设备”并按“+”以将其移至列表顶部。如果它无法通过“+”移动，只需选择“EFI 杂项设备”，然后按 Enter 键启动到它即可。</li>
      <li>提交这些更改并退出。</li>
      <li>
        MBM 应自动启动到卡（此初始启动可能需要 2 分钟，后续启动所需的时间应该会少于 30 秒）。否则，它会启动到 UEFI shell，此时你必须在 UEFI shell 中执行以下命令来启动 Windows：
        <kbd>fs1：</kbd><br/>
        <kbd>efi\boot\bootia32.efi</kbd>
      </li>
      <li>设备启动后，DefaultApp 将启动并显示 MBM 的 IP 地址。</li>
    </div>
    <div class="col-md-6 col-sm-12">
      <img src="{{site.baseurl}}/Resources/images/DefaultAppMBM.png">
    </div>
  </div>
</ol>
<p>如果已在 MBM 上加载以前版本的 IoT 核心版，将需要完成以下步骤才能完成首次启动（请确保已插入用于 IoT 核心版的 SD 卡）：</p>
<ol class="setup-content-list">
  <div class="row">
    <div class="col-md-6 col-sm-12">
      <li>打开 MBM 设备并按 F2。</li>
      <li>转到“启动管理器”，并选择“EFI Internal Shell”。</li>
      <li>标识 EFIESP 分区（它可能是 FS1：因此假设 EFIESP 分区为 FS1：如下）</li>
      <li>类型 FS1：</li>
      <li>Cd EFI</li>
      <li>运行 DeleteSbcpVariableFW.efi（这将清除 UEFI 变量）</li>
      <li>立即启动设备。</li>
    </div>
  </div>
</ol>
<h3>连接到设备</h3>
<ol class="setup-content-list">
  <div class="row">
    <div class="col-md-6 col-sm-12">
      <li>
        你可以使用 <a href="{{site.baseurl}}/{{page.lang}}/win10/tools/DevicePortal.htm" target="_blank">Windows Device Portal</a> 通过你最喜爱的 Web 浏览器来连接到设备。除了高级诊断工具外，设备门户还提供了配置和设备管理功能，从而帮助你排除 Windows IoT 设备的故障并查看其实时性能。<a href="{{site.baseurl}}/{{page.lang}}/win10/tools/DevicePortal.htm" target="_blank">单击此处以了解如何连接到 Windows Device Portal！</a>
      </li>
    </div>
    <div class="col-md-6 col-sm-12">
      <img class="device-images" src="{{site.baseurl}}/Resources/images/deviceportal/deviceportal_small_mbm.png">
    </div>
  </div>
  <div class="row">
    <div class="col-md-6 col-sm-12">
      <li>
        你还可以使用 PowerShell 通过命令外壳来连接到设备。按照 <a href="{{site.baseurl}}/{{page.lang}}/win10/samples/PowerShell.htm" target="_blank">PowerShell 文档</a>使用 PowerShell 来连接到正在运行的设备。 也可按照 <a href="{{site.baseurl}}/{{page.lang}}/win10/samples/SSH.htm" target="_blank">SSH 说明</a>使用 SSH 来连接到设备。
      </li>
    </div>
    <div class="col-md-6 col-sm-12">
      <img class="device-images" src="{{site.baseurl}}/Resources/images/powershell/connection.png">
    </div>
  </div>
</ol>
<div>
  强烈建议你更新 Administrator 帐户的默认密码。<a href="{{site.baseurl}}/{{page.lang}}/win10/tools/DevicePortal.htm" target="_blank">Windows Device Portal</a> 或 <a href="{{site.baseurl}}/{{page.lang}}/win10/samples/PowerShell.htm" target="_blank">Powershell</a> 的相关文档中有说明。
</div>
<h3> 其他资源 </h3>
<p><a href="{{site.baseurl}}/{{page.lang}}/win10/SupportedInterfaces.htm" target="_blank">受支持的外围接口和设备</a></p>
