# Checklist

- [x] index.html 为单文件纯 HTML（内联 CSS/JS），双击离线可玩，无外部依赖、无网络请求、无控制台报错（浏览器加载验证：console 无错误）
- [x] 场景包含：主角背影坐在电脑前、显示器滚动代码、桌上蓝色小鱼玩偶、巡逻的 Boss、1024 程序员节装饰（canvas 采样 74 种颜色，画面渲染丰富）
- [x] 顶部居中显示 1024 秒倒计时，剩余时间分档变色（绿→黄→橙→红），2 的幂里程碑有提示（timeColor 四档验证：#7CFC9A/#ffd76a/#ffa14e/#ff5a5a）
- [x] Boss 会行走、随机停留、回头面向主角；危险/安全状态通过朝向、表情/标记、音效清晰可辨（walk/pause/turn/watch/turnback 状态机 + front/side 两态验证）
- [x] Boss 背对时摸鱼可加速倒计时（速率 = 基础值 × 阶段倍率）；Boss 看向主角时摸鱼，反应窗口（约 0.5s）内松手安全、超时被抓（实测 1024→983.69 摸鱼加速；watchElapsedHold>0.5 触发 caught）
- [x] 被抓惩罚生效：倒计时回拨（如 +32s）、怀疑度 +1、Boss 训斥气泡、屏幕震动；怀疑度满 3 进入加班失败结局并可重开（实测回拨 983.69→1015.69、suspicion 满 3 切 LOSE）
- [x] 全部数值集中在 CONFIG 常量表（基础值 × 倍率系数）；最后 64 秒倍率降低、Boss 回头更频繁且注视更久、有紧张特效（三阶段实测：x8/x4/x2）
- [x] 摸鱼时小鱼抖动/形变、手来回搓动、摸鱼进度条抖动增长、周期性 "+N 秒" 漂浮文字（rubPhase 形变 + drawHand + addFloat 池）
- [x] 倒计时归零触发全屏烟花粒子 + 胜利结算（加成节省秒数、被抓次数、S/A/B/C 评级、再来一局）（实测 remain 耗尽切 WIN；评级 S/A/C 分档验证通过）
- [x] 标题页含游戏名《还有1024秒下班》、1024 副标题、玩法说明与开始按钮（TITLE 场景 + startRect 按钮验证）
- [x] WebAudio 程序化音效（摸鱼/预警/被抓/烟花）可静音，首次交互后才初始化（audioRub/audioAlert/audioCaught/audioWin + ensureAudio + muteRect）
- [x] 鼠标按住、触摸按住、空格按住三种输入均可摸鱼，画面随窗口尺寸自适应（Pointer Events 统一抽象 + Space 键 + fitCanvas 等比缩放）
