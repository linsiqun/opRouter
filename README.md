<div class="markdown-heading">
	<h1 class="heading-element">
		<strong>Router Deployment OP Installation Firmware</strong> 
	</h1>
<a id="user-content-router-deployment-op-installation-firmware" class="anchor" href="https://github.com/linsiqun/VSPdeployment/blob/main/VPSnodes.md#router-deployment-op-installation-firmware"></a>
</div>
<p style="text-indent:2em;">
	a. <a href="https://firmware-selector.immortalwrt.org/">https://firmware-selector.immortalwrt.org/</a>&nbsp; &nbsp; (Download the ImmortalWrt firmware for your device)
</p>
<p style="text-indent:2em;">
	b. <a href="https://github.com/jerrykuku/luci-theme-argon/">https://github.com/jerrykuku/luci-theme-argon/</a>&nbsp; &nbsp; (New OpenWrt LuCI theme)
</p>
<p style="text-indent:2em;">
	c. <a href="https://github.com/xiaorouji/openwrt-passwall/releases/">https://github.com/xiaorouji/openwrt-passwall/releases/</a>&nbsp; &nbsp; (passwall)
</p>
<p style="text-indent:2em;">
	d. <a href="https://github.com/vernesong/OpenClash?tab=readme-ov-file/">https://github.com/vernesong/OpenClash?tab=readme-ov-file/</a>&nbsp; &nbsp; (openclash)
</p>
<p style="text-indent:2em;">
	e. <a href="https://github.com/nikkinikki-org/OpenWrt-nikki/blob/main/README.zh.md">https://github.com/nikkinikki-org/OpenWrt-nikki/blob/main/README.zh.md</a>&nbsp; &nbsp; (nikki)
</p>
<p style="text-indent:2em;">
	<strong>1. To install all other package definitions, run: command&nbsp;</strong>(After installing the original OpenWrt version)
</p>
<p style="text-indent:2em;">
	<strong>The following command</strong>
</p>
<p style="text-indent:2em;">
	<br />
</p>
<p style="text-indent:2em;">
	./scripts/feeds update luci
</p>
<p style="text-indent:2em;">
	./scripts/feeds install -a -p luci
</p>
<p style="text-indent:2em;">
	<br />
</p>
<h1 class="heading-element" style="text-indent:2em;">
	<strong><span style="font-size:16px;color:#E53333;">Restart OpenWrt and refresh the packages</span><br />
</strong>
</h1>
<h1 class="heading-element" style="text-indent:2em;">
	<strong>passwall</strong>
</h1>
<p style="text-indent:2em;">
	<a id="user-content-passwall" class="anchor" href="https://github.com/linsiqun/VSPdeployment/blob/main/VPSnodes.md#passwall"></a>
</p>
<p style="text-indent:2em;">
	<br />
</p>
<p style="text-indent:2em;">
	<strong>2. Restart OpenWrt and refresh the software package</strong>
</p>
<p style="text-indent:2em;">
	<br />
</p>
<p style="text-indent:2em;">
	<br />
</p>
<p style="text-indent:2em;">
	<ol>
		<li>
			<p>
				Go to <a href="https://github.com/xiaorouji/openwrt-passwall/releases/passwall">https://github.com/xiaorouji/openwrt-passwall/releases/&nbsp;</a>&nbsp; &nbsp; &nbsp; &nbsp;<span>(</span><span>passwall<span>)</span></span> 
			</p>
		</li>
		<li>
			<p>
				Go to <a href="https://github.com/xiaorouji/openwrt-passwall2/releases/passwall2">https://github.com/xiaorouji/openwrt-passwall2/releases/&nbsp;</a>&nbsp; &nbsp; &nbsp;<span>(</span><span>passwall2<span>)</span></span> 
			</p>
		</li>
	</ol>
</p>
<p style="text-indent:2em;">
	<br />
</p>
<p style="text-indent:2em;">
	<br />
</p>
<p style="text-indent:2em;">
	Download luci-19.07_luci-app-passwall_25.7.4-1_all.ipk, rename it to luci-app-passwall_all.ipk, upload and install.
</p>
<p style="text-indent:2em;">
	Download 
luci-19.07_luci-i18n-passwall-zh-cn_25.7.4-1_all.ipk, rename it to 
luci-i18n-passwall-zh-cn_all.ipk, upload and install.
</p>
<div class="markdown-heading">
	<h1 class="heading-element">
		<strong>openClash</strong> 
	</h1>
<a id="user-content-openclash" class="anchor" href="https://github.com/linsiqun/VSPdeployment/blob/main/VPSnodes.md#openclash"></a>
</div>
<p style="text-indent:2em;">
	<strong>Restart OpenWrt</strong>
</p>
<p style="text-indent:2em;">
	<span style="color:#E53333;">Please install these dependencies first.</span>
</p>
<p style="text-indent:2em;">
	<strong>Deploy the following command</strong>
</p>
<p style="text-indent:2em;">
	<strong><br />
</strong>
</p>
<p style="text-indent:2em;">
	<strong></strong>
</p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto">
	<strong> 
<pre class="notranslate">#iptables
opkg update
opkg install bash iptables dnsmasq-full curl ca-bundle ipset ip-full iptables-mod-tproxy iptables-mod-extra ruby ruby-yaml kmod-tun kmod-inet-diag unzip luci-compat luci luci-base
opkg install /tmp/openclash.ipk

apk update
apk add bash iptables dnsmasq-full curl ca-bundle ipset ip-full iptables-mod-tproxy iptables-mod-extra ruby ruby-yaml kmod-tun kmod-inet-diag unzip luci-compat luci luci-base
apk add -q --force-overwrite --clean-protected --allow-untrusted /tmp/openclash.apk</pre>
	<div class="zeroclipboard-container position-absolute right-0 top-0">
	</div>
</strong>
</div>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto">
	<strong> 
<pre class="notranslate">#nftables
opkg update
opkg install bash dnsmasq-full curl ca-bundle ip-full ruby ruby-yaml kmod-tun kmod-inet-diag unzip kmod-nft-tproxy luci-compat luci luci-base
opkg install /tmp/openclash.ipk

apk update
apk add bash dnsmasq-full curl ca-bundle ip-full ruby ruby-yaml kmod-tun kmod-inet-diag unzip kmod-nft-tproxy luci-compat luci luci-base
apk add -q --force-overwrite --clean-protected --allow-untrusted /tmp/openclash.apk</pre>
</strong>
</div>
<p style="text-indent:2em;">
	<br />
</p>
<p style="text-indent:2em;">
	Install the above dependencies in order, installing each dependency separately.
</p>
<p style="text-indent:2em;">
	<a href="https://github.com/vernesong/OpenClash/releases">https://github.com/vernesong/OpenClash/releases</a>
</p>
<p style="text-indent:2em;">
	4.Next, download luci-app-openclash_0.46.115_all.ipk, rename it to luci-app-openclash_all.ipk, and upload it for installation.
</p>
<div class="markdown-heading">
	<h1 class="heading-element">
		<strong>nikki</strong> 
	</h1>
<a id="user-content-nikki" class="anchor" href="https://github.com/linsiqun/VSPdeployment/blob/main/VPSnodes.md#nikki"></a>
</div>
<p style="text-indent:2em;">
	Deployment Requirements
</p>
<p style="text-indent:2em;">
	<br />
</p>
<p style="text-indent:2em;">
	<ul>
		<li>
			OpenWrt &gt;= 23.05
		</li>
		<li>
			Linux Kernel &gt;= 5.13
		</li>
		<li>
			firewall4
		</li>
	</ul>
</p>
<p style="text-indent:2em;">
	<br />
</p>
<p style="text-indent:2em;">
	<strong>A.Installing from the Source Website (Recommended)</strong> <a href="https://github.com/nikkinikki-org/OpenWrt-nikki/blob/main/README.zh.md">https://github.com/nikkinikki-org/OpenWrt-nikki/blob/main/README.zh.md</a>
</p>
<div class="markdown-heading">
	<h1 class="heading-element">
		<span style="font-size:14px;color:#E53333;">Run only once</span> 
	</h1>
<a id="user-content-run-only-once" class="anchor" href="https://github.com/linsiqun/VSPdeployment/blob/main/VPSnodes.md#run-only-once"></a>
</div>
<p style="text-indent:2em;">
	<strong>Installation Commands</strong>
</p>
<p style="text-indent:2em;">
	<br />
</p>
<p style="text-indent:2em;">
	<ol>
		<li>
			Add&nbsp;
		</li>
	</ol>
</p>
<p style="text-indent:2em;">
	<br />
</p>
<div class="highlight highlight-source-shell notranslate position-relative overflow-auto">
<pre><span class="pl-c"><span class="pl-c">#</span> only needs to be run once</span> wget -O - https://github.com/nikkinikki-org/OpenWrt-nikki/raw/refs/heads/main/feed.sh <span class="pl-k">|</span> ash</pre>
	<div class="zeroclipboard-container">
	</div>
</div>
<p style="text-indent:2em;">
	<br />
</p>
<p style="text-indent:2em;">
	<ol>
		<li>
			Install
		</li>
	</ol>
</p>
<p style="text-indent:2em;">
	<br />
</p>
<div class="highlight highlight-source-shell notranslate position-relative overflow-auto">
<pre><span class="pl-c"><span class="pl-c">#</span> you can install from shell or `Software` menu in LuCI</span> <span class="pl-c"><span class="pl-c">#</span> for opkg</span> opkg install nikki
opkg install luci-app-nikki
opkg install luci-i18n-nikki-zh-cn <span class="pl-c"><span class="pl-c">#</span> for apk</span> apk add nikki
apk add luci-app-nikki
apk add luci-i18n-nikki-zh-cn</pre>
</div>
<h3 class="heading-element" style="text-indent:2em;">
	<br />
</h3>
<h3 class="heading-element" style="text-indent:2em;">
	B. Install From Release
</h3>
<p style="text-indent:2em;">
	<a id="user-content-b-install-from-release" class="anchor" href="https://github.com/nikkinikki-org/OpenWrt-nikki/blob/main/README.md#b-install-from-release"></a>
</p>
<p style="text-indent:2em;">
	<br />
</p>
<p style="text-indent:2em;">
<pre>wget -O - https://github.com/nikkinikki-org/OpenWrt-nikki/raw/refs/heads/main/install.sh <span class="pl-k">|</span> ash</pre>
</p>
<p style="text-indent:2em;">
	<br />
</p>
<div class="zeroclipboard-container">
</div>
<div class="markdown-heading">
	<h2 class="heading-element">
		Uninstall &amp; Reset
	</h2>
<a id="user-content-uninstall--reset" class="anchor" href="https://github.com/nikkinikki-org/OpenWrt-nikki/blob/main/README.md#uninstall--reset"></a>
</div>
<p style="text-indent:2em;">
	<br />
</p>
<p style="text-indent:2em;">
<pre>wget -O - https://github.com/nikkinikki-org/OpenWrt-nikki/raw/refs/heads/main/uninstall.sh <span class="pl-k">|</span> ash</pre>
<p style="text-indent:2em;">
	<br />
</p>
<p style="text-indent:2em;">
<strong> 
	<div class="zeroclipboard-container">
	</div>
	<div class="markdown-heading">
		<h2 class="heading-element">
			How To Use
		</h2>
<a id="user-content-how-to-use" class="anchor" href="https://github.com/nikkinikki-org/OpenWrt-nikki/blob/main/README.md#how-to-use"></a> 
	</div>
	<p>
		See <a href="https://github.com/nikkinikki-org/OpenWrt-nikki/wiki">Wiki</a> 
	</p>
	<div class="markdown-heading">
		<h2 class="heading-element">
			How does it work
		</h2>
<a id="user-content-how-does-it-work" class="anchor" href="https://github.com/nikkinikki-org/OpenWrt-nikki/blob/main/README.md#how-does-it-work"></a> 
	</div>
	<ol>
		<li>
			Mixin and Update profile.
		</li>
		<li>
			Run mihomo.
		</li>
		<li>
			Set scheduled restart.
		</li>
		<li>
			Set ip rule/route
		</li>
		<li>
			Generate nftables and apply it.
		</li>
	</ol>
	<p>
		Note that the steps above may change base on config.
	</p>
	<p>
		<br />
	</p>
	<h2 class="heading-element">
		Compilation <span style="color:#E53333;font-size:14px;">Deploy the following command</span> 
	</h2>
	<h2 class="heading-element">
		<span class="pl-c" style="font-size:12px;"><span class="pl-c"> 
<pre>

<pre># add feed
echo "src-git nikki https://github.com/nikkinikki-org/OpenWrt-nikki.git;main" &gt;&gt; "feeds.conf.default"
# update &amp; install feeds
./scripts/feeds update -a
./scripts/feeds install -a
# make package
make package/luci-app-nikki/compile
</pre>
</pre>
</span></span> 
	</h2>
	<p>
		The package files will be found underbin/packages/your_architecture/nikki.
	</p>
	<div class="markdown-heading">
		<h2 class="heading-element">
			Dependencies
		</h2>
<a id="user-content-dependencies" class="anchor" href="https://github.com/nikkinikki-org/OpenWrt-nikki/blob/main/README.md#dependencies"></a> 
	</div>
	<ul>
		<li>
			ca-bundle
		</li>
		<li>
			curl
		</li>
		<li>
			yq
		</li>
		<li>
			firewall4
		</li>
		<li>
			ip-full
		</li>
		<li>
			kmod-inet-diag
		</li>
		<li>
			kmod-nft-socket
		</li>
		<li>
			kmod-nft-tproxy
		</li>
		<li>
			kmod-tun
		</li>
	</ul>
</strong>
</p>
<p style="text-indent:2em;">
	<br />
</p>
<h1 class="heading-element" style="text-indent:2em;">
	<strong>OpenWrt LuCI Theme</strong>
</h1>
<p style="text-indent:2em;">
	<a href="https://github.com/jerrykuku/luci-theme-argon/">https://github.com/jerrykuku/luci-theme-argon</a><span style="font-size:12px;font-weight:normal;">/&nbsp;</span><strong>Brand new OpenWrt LuCI theme</strong>
</p>
<p style="text-indent:2em;">
	<br />
</p>
<p style="text-indent:2em;">
	<strong><span class="HwtZe" style="font-size:10px;background-color:#E53333;"><span style="background-color:#FFFFFF;color:#E53333;">The following command</span></span></strong>
</p>
<p style="text-indent:2em;">
	<br />
</p>
<p style="text-indent:2em;">
	<strong>Deployment Commands</strong>&nbsp; <span>(</span>opkg<span>)</span>
</p>
<p style="text-indent:2em;">
	<span style="background-color:#FFFFFF;">opkg update #Refresh the package source</span>
</p>
<p style="text-indent:2em;">
	<span style="background-color:#FFFFFF;">opkg install pkg #Install a specific package</span>
</p>
<p style="text-indent:2em;">
	<span style="background-color:#FFFFFF;">opkg remove pkg #Uninstall a specific package</span><span style="background-color:;"></span>
</p>
<p style="text-indent:2em;">
	<strong><br />
</strong>
</p>
<p style="text-indent:2em;">
	<strong>Deployment Commands</strong> <span>(</span>apk<span>)</span>
</p>
<p style="text-indent:2em;">
	<span style="background-color:#FFFFFF;">apk update #Refresh the package source</span>
</p>
<p style="text-indent:2em;">
	<span style="background-color:#FFFFFF;">apk add pkg #Install a specific package</span>
</p>
<p style="text-indent:2em;">
	<span style="background-color:#FFFFFF;">apk del pkg #Uninstall a specific package</span>
</p>
<p style="text-indent:2em;">
	<br />
</p>
<h1 class="heading-element" style="text-indent:2em;">
	<span style="font-size:24px;font-weight:normal;"><strong>The following command</strong></span>
</h1>
<p style="text-indent:2em;">
	<a id="user-content-deployment-commands" class="anchor" href="https://github.com/linsiqun/VSPdeployment/blob/main/VPSnodes.md#deployment-commands"></a>
</p>
<p style="text-indent:2em;">
	<br />
</p>
<p style="text-indent:2em;">
	<strong></strong>
</p>
<div class="markdown-heading">
	<h3 class="heading-element">
		<strong><span class="HwtZe">Building for OpenWrt official SnapShots and ImmortalWrt</span></strong> 
	</h3>
<strong><a id="user-content-build-for-openwrt-official-snapshots-and-immortalwrt" class="anchor" href="https://github.com/jerrykuku/luci-theme-argon#build-for-openwrt-official-snapshots-and-immortalwrt"></a></strong>
</div>
<p style="text-indent:2em;">
	<strong> </strong>
</p>
<p style="text-indent:2em;">
	<br />
</p>
<p style="text-indent:2em;">
<pre><strong><span class="pl-c1">cd</span> openwrt/package
git clone https://github.com/jerrykuku/luci-theme-argon.git
make menuconfig <span class="pl-c"><span class="pl-c">#</span>choose LUCI-&gt;Theme-&gt;Luci-theme-argon</span> make -j1 V=s</strong></pre>
<strong> 
	<div class="zeroclipboard-container">
	</div>
	<div class="markdown-heading">
		<h3 class="heading-element">
			<span class="HwtZe">Installing LuCI 18.06 (Lean LEDE)</span> 
		</h3>
<a id="user-content-install-for-luci-1806--leans-lede-" class="anchor" href="https://github.com/jerrykuku/luci-theme-argon#install-for-luci-1806--leans-lede-"></a> 
	</div>
<pre>wget --no-check-certificate https://github.com/jerrykuku/luci-theme-argon/releases/download/v1.8.2/luci-theme-argon_1.8.2-20230609_all.ipk
opkg install luci-theme-argon<span class="pl-k">*</span>.ipk</pre>
	<div class="zeroclipboard-container">
	</div>
	<div class="markdown-heading">
		<h3 class="heading-element">
			<span class="HwtZe">Install OpenWrt's official SnapShots and ImmortalWrt</span> 
		</h3>
<a id="user-content-install-for-openwrt-official-snapshots-and-immortalwrt" class="anchor" href="https://github.com/jerrykuku/luci-theme-argon#install-for-openwrt-official-snapshots-and-immortalwrt"></a> 
	</div>
<pre>opkg install luci-compat
opkg install luci-lib-ipkg
wget --no-check-certificate https://github.com/jerrykuku/luci-theme-argon/releases/download/v2.3.2/luci-theme-argon_2.3.2-r20250207_all.ipk
opkg install luci-theme-argon<span class="pl-k">*</span>.ipk</pre>
	<div class="zeroclipboard-container">
	</div>
	<div class="markdown-heading">
		<h3 class="heading-element">
			<span class="HwtZe">Install luci-app-argon-config</span> 
		</h3>
<a id="user-content-install-luci-app-argon-config" class="anchor" href="https://github.com/jerrykuku/luci-theme-argon#install-luci-app-argon-config"></a> 
	</div>
<pre>wget --no-check-certificate -O luci-app-argon-config_0.9_all.ipk https://github.com/jerrykuku/luci-app-argon-config/releases/download/v0.9/luci-app-argon-config_0.9_all.ipk
opkg install luci-app-argon-config<span class="pl-k">*</span>.ipk</pre>
</strong>
</p>
<p style="text-indent:2em;">
	<br />
</p>
<p style="text-indent:2em;">
	<a href="https://github.com/jerrykuku/luci-app-argon-config/releases/download/v0.9/luci-app-argon-config_0.9_all.apk"></a>
</p>
<div class="markdown-heading">
	<h1 class="heading-element">
		Skin Download
	</h1>
<a id="user-content-skin-download" class="anchor" href="https://github.com/linsiqun/VSPdeployment/blob/main/VPSnodes.md#skin-download"></a>
</div>
<p style="text-indent:2em;">
	from <a href="https://github.com/jerrykuku/luci-app-argon-config/releases/">https://github.com/jerrykuku/luci-app-argon-config/releases/</a>&nbsp; &nbsp;
</p>
<p style="text-indent:2em;">
	<span>Next, download 
luci-i18n-argon-config-zh-cn_git-22.114.24542-d1474ba_all.ipk Rename it 
to luci-i18n-argon-config-cn.ipk and upload it for installation.</span>
</p>
<p style="text-indent:2em;">
 from <a href="https://github.com/jerrykuku/luci-theme-argon/releases/">https://github.com/jerrykuku/luci-theme-argon/releases/</a><span>&nbsp; &nbsp;&nbsp;</span>
</p>
<p style="text-indent:2em;">
	Next, download luci-theme-argon-2.4.3-r20250722.apk , rename it to luci-theme-argon.apk and upload it for installation.
</p>
<div class="markdown-heading">
	<h1 class="heading-element">
		<span style="color:#E53333;font-size:14px;">deployment commands</span> 
	</h1>
<a id="user-content-deployment-commands-1" class="anchor" href="https://github.com/linsiqun/VSPdeployment/blob/main/VPSnodes.md#deployment-commands-1"></a>
</div>
<p style="text-indent:2em;">
	# Enter the kernel installation directory
</p>
<p style="text-indent:2em;">
	cd /etc/openclash/core/clash_meta
</p>
<p style="text-indent:2em;">
	# Download the kernel installation package
</p>
<p style="text-indent:2em;">
	wget <a href="https://raw.githubusercontent.com/vernesong/OpenClash/core/dev/smart/clash-linux-amd64-v1.tar.gz">https://raw.githubusercontent.com/vernesong/OpenClash/core/dev/smart/clash-linux-amd64-v1.tar.gz</a>
</p>
<p style="text-indent:2em;">
	# Unzip the kernel installation package
</p>
<p style="text-indent:2em;">
	tar -zxvf clash-linux-amd64-v1.tar.gz
</p>
<p style="text-indent:2em;">
	#Grant highest authority
</p>
<p style="text-indent:2em;">
	chmod 777 clash
</p>
