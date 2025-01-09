<template>
  <div>
    <h2 style="text-align: center; margin-top: 20px;">客户端下载</h2>
    <el-card class="center-card">
      <el-collapse accordion v-model="activeSection">
        <!-- 遍历大板块（Android TV / iOS / tvOS / Android / Windows / macOS / 路由器 等） -->
        <el-collapse-item
            v-for="(section, index) in proxyClientSections"
            :key="section.id"
            :title="section.title"
            :name="section.id"
        >
          <ul>
            <!-- 遍历每个板块中的条目 -->
            <li v-for="(item, idx) in section.items" :key="idx">
              <el-link
                  v-show="item.link"
                  :href="item.link"
                  target="_blank"
                  type="primary"
              >
                {{ item.text }}
              </el-link>
              <span v-show="!item.link">{{ item.text }}</span>
              <!-- 如果有 desc 就显示在后面 -->
              <span v-show="item.desc">（{{ item.desc }}）</span>
            </li>
          </ul>
        </el-collapse-item>
      </el-collapse>
    </el-card>
  </div>
</template>

<script>
export default {
  name: "MyExtractedPage",
  data() {
    return {
      // 用于控制手风琴展开的值
      activeSection: [
        'android_tv',
        'ios_all',
        'ios_other_region',
        'tvos_client',
        'android_client',
        'windows_client',
        'macos_client',
        'router'
      ],

      // Telegram 客户端 Proxy 代理设置
      telegramProxySetting: {
        title: "Telegram 客户端 Proxy 代理设置",
        imageLink: "https://cdn.jsdelivr.net/gh/youshandefeiyang/webcdn@6.4/tg.png",
        linkText: "点击查看",
      },

      /**
       * 代理客户端：将原始 HTML 中“代理客户端”下的各分类
       * (Android TV, iOS, tvOS, Android, Windows, macOS, 路由器...)
       * 抽取到一个数组里，每个板块包含 title / id / items 三部分。
       */
      proxyClientSections: [
        // 1) Android TV（包括国行索尼电视、FireTv系列）
        {
          id: "android_tv",
          title: "Android TV（包括国行索尼电视、FireTv系列）",
          items: [
            {
              text: "Sing-Box索尼电视兼容版",
              link: "https://github.com/SagerNet/sing-box/releases/latest",
              desc: "选择SFA-版本号-universal.apk",
            },
            {
              text: "Clash索尼电视兼容版",
              link: "https://t.me/feiyangdigital/529168",
            },
            {
              text: "v2rayNG索尼电视兼容版",
              link: "https://github.com/2dust/v2rayNG/releases/download/1.7.16/v2rayNG_1.7.16.apk",
            },
            {
              text: "Shadowsocks 影梭",
              link: "https://github.com/shadowsocks/shadowsocks-android/releases",
              desc: "选择shadowsocks-tv--universal",
            },
          ],
        },

        // 2) iOS 客户端 (全区可下载, 包括中区)
        {
          id: "ios_all",
          title: "iOS 客户端 (全区可下载，包括中区)",
          items: [
            {
              text: "Outline",
              link: "https://apps.apple.com/cn/app/outline-app/id1356177741",
              desc: "支持SS",
            },
          ],
        },

        // 3) iOS 客户端 (中区无法下载, 其他区可下载)
        {
          id: "ios_other_region",
          title: "iOS 客户端 (中区无法下载，其他区可下载)",
          items: [
            {
              text: "Surge iOS 5",
              link: "https://apps.apple.com/us/app/id1442620678?l=zh-cn",
              desc: "首年: $49.99, 次年开始: $14.99/年 (支持多协议)",
            },
            {
              text: "Quantumult X",
              link: "https://apps.apple.com/us/app/quantumult-x/id1443988620?l=zh-cn&platform=iphone",
              desc: "$7.99 (支持SS/SSR/VMess/VMessAEAD/Trojan)",
            },
            {
              text: "Shadowrocket (小火箭)",
              link: "https://apps.apple.com/us/app/shadowrocket/id932747118?l=zh-cn",
              desc: "$2.99 (支持SS/SSR/Snell/VMess/VMessAEAD/Trojan等)",
            },
            {
              text: "Loon",
              link: "https://apps.apple.com/us/app/loon/id1373567447?l=zh-cn",
              desc: "$5.99 (支持SS/SSR/VMess等)",
            },
            {
              text: "Loon Lite",
              link: "https://apps.apple.com/us/app/loon-lite/id6444029612?l=zh-cn",
              desc: "$0.99",
            },
            {
              text: "Stash (iOS 上的 Clash)",
              link: "https://apps.apple.com/us/app/stash-proxy-utility/id1596063349?l=zh-cn",
              desc: "$3.99 (支持多协议)",
            },
            {
              text: "Choc (iOS 上的 Clash)",
              link: "https://apps.apple.com/us/app/choc/id1582542227?l=zh-cn",
              desc: "$2.99",
            },
            {
              text: "Maomi (TestFlight)",
              link: "https://testflight.apple.com/join/LAn6mLkU",
              desc: "iOS 上的 Clash (Clash Premium 内核)",
            },
            {
              text: "sing-box",
              link: "https://apps.apple.com/us/app/sing-box/id6451272673?l=zh-cn",
              desc: "Free (支持SOCKS/HTTP/SS/SSR/VMess/Trojan/WireGuard等)",
            },
            {
              text: "Egern",
              link: "https://apps.apple.com/us/app/egern/id1616105820?l=zh-cn",
              desc: "$2.99 (支持SS/Trojan)",
            },
            {
              text: "Blatu",
              link: "https://apps.apple.com/us/app/blatu/id1317522797?l=zh-cn",
              desc: "$1.99 (Shadowrocket作者开发, 支持shadowvpn/DSVPN/WireGuard)",
            },
            {
              text: "Pharos Pro",
              link: "https://apps.apple.com/us/app/pharos-pro/id1456610173?l=zh-cn",
              desc: "$1.99",
            },
            {
              text: "Kitsunebi",
              link: "https://apps.apple.com/us/app/kitsunebi-proxy-utility/id1446584073",
              desc: "$4.99",
            },
            {
              text: "Potatso 2",
              link: "https://apps.apple.com/us/app/id1162704202",
              desc: "$2.99",
            },
            {
              text: "Potatso Lite",
              link: "https://apps.apple.com/us/app/id1239860606",
              desc: "Free",
            },
            {
              text: "LanceX",
              link: "https://apps.apple.com/us/app/lancex/id1536754048",
              desc: "$2.99",
            },
            {
              text: "TrojanX",
              link: "https://apps.apple.com/us/app/trojanx/id1523269113",
              desc: "$1.99",
            },
            {
              text: "OneClick",
              link: "https://apps.apple.com/us/app/id1545555197",
              desc: "Free",
            },
            {
              text: "Spectre VPN",
              link: "https://apps.apple.com/app/spectre-vpn/id1508712998",
              desc: "Free",
            },
            {
              text: "代购/人民币购买地址",
              link: "https://fk.myue.club",
            },
          ],
        },

        // 4) tvOS 客户端
        {
          id: "tvos_client",
          title: "tvOS 客户端",
          items: [
            {text: "Surge"},
            {text: "sing-box"},
            {text: "Quantumult X"},
            {text: "Shadowrocket"},
            {text: "Loon"},
            {text: "Loon Lite"},
            {text: "Stash"},
            {text: "Potatso"},
          ],
        },

        // 5) Android / 安卓 客户端
        {
          id: "android_client",
          title: "Android/安卓 客户端",
          items: [
            {
              text: "Surfboard",
              link: "https://github.com/getsurfboard/surfboard/releases",
              desc: "支持SS/VMess/Trojan, 可导入Surge配置",
            },
            {
              text: "Surfboard (Google Play)",
              link: "https://play.google.com/store/apps/details?id=com.getsurfboard",
            },
            {
              text: "sing-box",
              link: "https://github.com/SagerNet/sing-box/releases",
              desc: "支持多协议",
            },
            {
              text: "SagerNet (Google Play)",
              link: "https://play.google.com/store/apps/details?id=io.nekohasekai.sagernet",
            },
            {
              text: "Matsuri(茉莉)",
              link: "https://github.com/MatsuriDayo/Matsuri/releases",
            },
            {
              text: "AnXray",
              link: "https://github.com/XTLS/AnXray/releases",
            },
            {
              text: "Pharos",
              link: "https://github.com/PharosVip/Pharos-Android-Test/releases",
            },
            {
              text: "Kitsunebi",
              link: "https://github.com/eycorsican/kitsunebi-android/releases",
            },
            {
              text: "Kitsunebi (Google Play)",
              link: "https://play.google.com/store/apps/details?id=fun.kitsunebi.kitsunebi4android",
            },
            {
              text: "Shadowsocks 影梭",
              link: "https://github.com/shadowsocks/shadowsocks-android/releases",
            },
            {
              text: "Shadowsocks 影梭 (Google Play)",
              link: "https://play.google.com/store/apps/details?id=com.github.shadowsocks",
            },
            {
              text: "Shadowsocks 影梭 (Beta)",
              link: "https://play.google.com/apps/testing/com.github.shadowsocks",
            },
            {
              text: "Simple Obfuscation (插件)",
              link: "https://github.com/shadowsocks/simple-obfs-android/releases",
            },
            {
              text: "Simple Obfuscation (Google Play)",
              link: "https://play.google.com/store/apps/details?id=com.github.shadowsocks.plugin.obfs_local",
            },
            {
              text: "v2rayNG",
              link: "https://github.com/2dust/v2rayNG/releases",
            },
            {
              text: "v2rayNG (Google Play)",
              link: "https://play.google.com/store/apps/details?id=com.v2ray.ang",
            },
            {
              text: "NekoBox for Android",
              link: "https://play.google.com/store/apps/details?id=moe.nb4a",
            },
            {
              text: "NekoBoxForAndroid",
              link: "https://github.com/MatsuriDayo/NekoBoxForAndroid/releases",
            },
            {
              text: "OneClick",
              link: "https://oneclick.earth/files/app-website-release.apk",
            },
            {
              text: "OneClick (Google Play)",
              link: "https://play.google.com/store/apps/details?id=earth.oneclick",
            },
            {
              text: "Clash for Magisk",
              link: "https://github.com/kalasutra/Clash_For_Magisk",
            },
            {
              text: "SBA",
              link: "https://play.google.com/store/apps/details?id=com.github.douglarek.sba",
            },
          ],
        },

        // 6) Windows 客户端
        {
          id: "windows_client",
          title: "Windows 客户端",
          items: [
            {
              text: "sing-box",
              link: "https://apps.apple.com/us/app/sing-box/id6451272673",
              desc: "支持多协议",
            },
            {
              text: "Netch",
              link: "https://github.com/netchx/Netch/releases",
              desc: "支持SS/SSR/Vmess",
            },
            {
              text: "WinXray",
              link: "https://github.com/TheMRLL/winxray/releases",
            },
            {
              text: "NekoRay",
              link: "https://github.com/MatsuriDayo/nekoray/releases",
            },
            {
              text: "XrayR",
              link: "https://github.com/XrayR-project/XrayR/releases",
            },
            {
              text: "Shadowsocks (SS)",
              link: "https://github.com/shadowsocks/shadowsocks-windows/releases",
            },
            {
              text: "simple-obfs (SS插件)",
              link: "https://github.com/shadowsocks/simple-obfs/releases",
            },
            {
              text: "Shadowsocks 2.3.1 (XP可用)",
              link: "https://github.com/shadowsocks/shadowsocks-windows/releases/tag/2.3.1",
            },
            {
              text: "v2rayN",
              link: "https://github.com/2dust/v2rayN/releases",
            },
            {
              text: "V2RayW",
              link: "https://github.com/Cenmrev/V2RayW/releases",
            },
            {
              text: "V2RayS",
              link: "https://github.com/Shinlor/V2RayS/releases",
            },
            {
              text: "Qv2ray",
              link: "https://github.com/Qv2ray/Qv2ray/releases",
            },
            {
              text: "Maple",
              link: "https://github.com/YtFlow/Maple/releases",
            },
            {
              text: "Shadowsocks Electron",
              link: "https://github.com/nojsja/shadowsocks-electron/releases",
            },
          ],
        },

        // 7) macOS 客户端
        {
          id: "macos_client",
          title: "macOS 客户端",
          items: [
            {
              text: "Surge Mac 5",
              link: "https://nssurge.com/buy_now",
              desc: "$49.99 / $69.99 / $99.99 (支持多协议)",
            },
            {
              text: "Quantumult X (macOS)",
              link: "https://apps.apple.com/us/app/quantumult-x/id1443988620?l=zh-cn&platform=mac",
              desc: "$7.99 (支持SS/SSR/VMess等, 需 macOS 11+)",
            },
            {
              text: "Stash for macOS",
              link: "https://stash.ws/macos/pricing/",
              desc: "专为macOS设计, 比iOS版功能更丰富",
            },
            {
              text: "XrayR",
              link: "https://github.com/XrayR-project/XrayR/releases",
            },
            {
              text: "V2RayX",
              link: "https://github.com/Cenmrev/V2RayX/releases",
            },
            {
              text: "V2rayU",
              link: "https://github.com/yanue/V2rayU/releases",
            },
            {
              text: "V2RayC",
              link: "https://github.com/gssdromen/V2RayC",
            },
            {
              text: "Qv2ray",
              link: "https://github.com/Qv2ray/Qv2ray/releases",
            },
            {
              text: "TrojanX",
              link: "https://github.com/JimLee1996/TrojanX/releases",
            },
            {
              text: "Shadowsocks Electron",
              link: "https://github.com/nojsja/shadowsocks-electron/releases",
            },
          ],
        },

        // 8) 路由器
        {
          id: "router",
          title: "路由器",
          items: [
            {
              text: "iStore-OS插件仓库",
              link: "https://github.com/AUK9527/Are-u-ok",
            },
            {
              text: "Koolshare OpenWrt/LED (KoolClash)",
              link: "https://koolclash.js.org",
            },
            {
              text: "fancyss",
              link: "https://github.com/hq450/fancyss",
            },
            {
              text: "OpenWRT-Shadowsocks",
              link: "https://github.com/shadowsocks/openwrt-shadowsocks",
            },
            {
              text: "Padavan",
              link: "https://www.right.com.cn/forum/thread-161324-1-1.html",
            },
          ],
        },
      ],
    };
  },
};
</script>

<style scoped>
.center-card {
  width: 60%;
  margin: 0 auto; /* This centers the card horizontally */
}

</style>
