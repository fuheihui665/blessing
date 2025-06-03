
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>端午祝福语</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link href="https://cdn.jsdelivr.net/npm/font-awesome@4.7.0/css/font-awesome.min.css" rel="stylesheet">
  
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            primary: '#165DFF',
            success: '#00B42A',
            neutral: '#F5F7FA',
            'neutral-light': '#F9FAFB',
          },
          fontFamily: {
            inter: ['Inter', 'system-ui', 'sans-serif'],
          },
          boxShadow: {
            'micro': '0 1px 4px rgba(0,0,0,0.05)',
          },
          borderRadius: {
            'sm': '4px',
          }
        },
      }
    }
  </script>
  
  <style type="text/tailwindcss">
    body {
      overscroll-behavior: none;
    }
    .blessing-card {
      transition: transform 0.2s ease, box-shadow 0.2s ease;
    }
    .blessing-card:hover {
      transform: translateX(4px);
      box-shadow: 0 2px 8px rgba(22, 93, 255, 0.1);
    }
  </style>
</head>
<body class="font-inter bg-neutral-light min-h-screen">



  <main class="max-w-6xl mx-auto px-4 pb-12">
    <div class="grid grid-cols-1 gap-3" id="blessingContainer">
      <!-- 祝福语卡片动态生成 -->
    </div>
  </main>

  <footer class="bg-white border-t border-gray-200 py-3">
    <div class="text-center text-xs text-gray-500">
       祝福语工具     </div>
  </footer>

  <div id="toast" class="fixed bottom-6 left-1/2 transform -translate-x-1/2 bg-success text-white px-4 py-2 rounded-sm shadow-md opacity-0 transition-opacity duration-300">
    <i class="fa fa-check mr-1"></i>
    <span>已复制</span>
  </div>

  <script>
    // 完整的100条祝福语数据
    const blessings = [
      { id: 1, content: "祝大家端午安康" },
      { id: 2, content: "香囊寄思" },
      { id: 3, content: "粽子飘香" },
      { id: 4, content: "万树千山粽是情" },
      { id: 5, content: "送你一颗好运粽" },
      { id: 6, content: "五月五赛龙舟" },
      { id: 7, content: "好的东西就需要分享" },
      { id: 8, content: "愿幸福的粽叶裹住你" },
      { id: 9, content: "送你一只香甜粽子" },
      { id: 10, content: "想拉着你的手一起看龙舟" },
      { id: 11, content: "禁止端午节不理我" },
      { id: 12, content: "今年送你的粽子不一般" },
      { id: 13, content: "祝你端午吉祥如意" },
      { id: 14, content: "希望你粽是幸运" },
      { id: 15, content: "蒲月初五是端午" },
      { id: 16, content: "青绿的粽叶包裹浓浓的真情" },
      { id: 17, content: "五色的丝线迎风飞舞" },
      { id: 18, content: "五色新丝缠角粽" },
      { id: 19, content: "汨罗江在诉说着一段神奇的故事" },
      { id: 20, content: "又是佳节好时光" },
      { id: 21, content: "热烈龙舟划动着千年的祈愿" },
      { id: 22, content: "愿你品尝出人生的夸姣和蒲月五的情怀" },
      { id: 23, content: "吃的是粽子甜的是生活" },
      { id: 24, content: "长长丝线绑健康" },
      { id: 25, content: "六月的轻风飘来淡淡的粽香" },
      { id: 26, content: "甜甜粽馅溢飘香" },
      { id: 27, content: "希望祝福能随着艾叶的淡淡清香飘到你那里" },
      { id: 28, content: "赛舟驰骋处处祥" },
      { id: 29, content: "汨罗江在诉说着一段传奇的故事" },
      { id: 30, content: "五月端午粽糕飘香" },
      { id: 31, content: "粽叶艾草继续着不变的清香" },
      { id: 32, content: "投粽江河喂鱼以祭屈原" },
      { id: 33, content: "片片艾叶片片情" },
      { id: 34, content: "温婉甜粽在线打call" },
      { id: 35, content: "咸甜之争烽烟再起" },
      { id: 36, content: "只有油润不腻味道香甜的肉粽才是王道" },
      { id: 37, content: "深红色的咸肉泛着油光" },
      { id: 38, content: "咬上一口仿佛时间都静止了" },
      { id: 39, content: "还有鲜香无比的蛋黄肉粽" },
      { id: 40, content: "丰富的口感让我欲罢不能" },
      { id: 41, content: "肉粽知道灵魂的去处" },
      { id: 42, content: "肉粽党发言完毕" },
      { id: 43, content: "清清爽爽的甜粽才是人间值得" },
      { id: 44, content: "雪白的糯米包着甜甜的蜜枣" },
      { id: 45, content: "一定要让粽子在凉水里冷静一下" },
      { id: 46, content: "粘上点白糖就更绝了" },
      { id: 47, content: "白糖会使糯米更加的香甜弹牙" },
      { id: 48, content: "那种幸福从脚尖直冲到天灵盖的感觉" },
      { id: 49, content: "永生都难以忘记" },
      { id: 50, content: "甜粽党发言完毕" },
      { id: 51, content: "到底是甜粽还是咸粽呢" },
      { id: 52, content: "我觉得你要比粽子甜上那么一点" },
      { id: 53, content: "乘着龙舟给你捎来端午的问候" },
      { id: 54, content: "清香的叶子层层叠叠" },
      { id: 55, content: "祝你健康平安过个清清凉凉的夏天" },
      { id: 56, content: "红红的樱桃红红的枣" },
      { id: 57, content: "用艾叶把烦恼都赶跑" },
      { id: 58, content: "愿你拥有人间最美好最珍贵的一切" },
      { id: 59, content: "五月初五恰逢端阳" },
      { id: 60, content: "端午的祝福悄然而至" },
      { id: 61, content: "小小的粽子里藏着我最真的心意" },
      { id: 62, content: "愿你平安喜乐" },
      { id: 63, content: "在江面的龙舟上再续永恒的主题" },
      { id: 64, content: "相比粽子的甜咸我在意的是假期的长短" },
      { id: 65, content: "汨罗江中藏着一位先贤的故事" },
      { id: 66, content: "一层层的粽叶包裹的都是生活的香甜" },
      { id: 67, content: "整个六月都飘着艾叶配粽子的香气" },
      { id: 68, content: "我永远支持甜粽" },
      { id: 69, content: "没什么好说的粽子就该是咸的" },
      { id: 70, content: "祝福语伴着春风来了" },
      { id: 71, content: "甜的咸的其实都行" },
      { id: 72, content: "让我们一起干了这杯雄黄酒" },
      { id: 73, content: "这枚香袋是我亲手做的" },
      { id: 74, content: "用千娇百媚的芭蕉叶把你轻轻包裹" },
      { id: 75, content: "让纸鸢带着我的祝福飞向你" },
      { id: 76, content: "挂着彩绳放风筝是端午最开心的事了" },
      { id: 77, content: "平安吉祥端午安康" },
      { id: 78, content: "艾蒿高高门前舞" },
      { id: 79, content: "苇叶和糯米也包含着对屈原的无限敬意" },
      { id: 80, content: "路漫漫其修远兮" },
      { id: 81, content: "吾将上下而求索" },
      { id: 82, content: "吃粽子的同时也要记得驱五毒哦" },
      { id: 83, content: "万人齐赛龙舟真是再壮观不过了" },
      { id: 84, content: "这五彩的丝线缠着的是我的无尽牵挂" },
      { id: 85, content: "我可是最棒的龙舟手" },
      { id: 86, content: "希望你的六月有西瓜的清凉" },
      { id: 87, content: "说实话咸的我能吃甜的我也可以" },
      { id: 88, content: "希望六月能善待你" },
      { id: 89, content: "一株暗香四溢的艾草传递着我的情意" },
      { id: 90, content: "端午假期能见到你才是最幸福的事" },
      { id: 91, content: "粽子和我的爱意一样都是甜的" },
      { id: 92, content: "清润端阳节" },
      { id: 93, content: "茅檐插艾新" },
      { id: 94, content: "浴兰包粽念忠臣" },
      { id: 95, content: "千古不亡湘水身" },
      { id: 96, content: "甜的咸的我都吃" },
      { id: 97, content: "咸蛋黄遇见白糯米" },
      { id: 98, content: "幸运的我遇见最好的你" },
      { id: 99, content: "我从咸粽区来看甜粽区的你" },
      { id: 100, content: "五彩绳缠住了思念" },
    ];

    // 渲染函数
    function renderBlessings() {
      const container = document.getElementById('blessingContainer');
      container.innerHTML = blessings.map(blessing => `
        <div class="blessing-card bg-white rounded-sm shadow-micro p-3">
          <div class="flex items-center mb-2">
            <div class="w-6 h-6 bg-primary/10 rounded-full flex items-center justify-center mr-2">
              <span class="text-primary font-semibold text-xs">${blessing.id}</span>
            </div>
            <p class="text-gray-800 text-xs ${blessing.content === '无' ? 'text-gray-400 italic' : ''}">
              ${blessing.content || '（无内容）'}
            </p>
          </div>
          <div class="flex justify-between items-center">
            <span class="text-xs text-gray-400">ID: ${blessing.id.toString().padStart(3, '0')}</span>
            <button class="copy-btn px-8 py-3 bg-primary text-white text-xs rounded-sm" data-id="${blessing.id}">
              <i class="fa fa-copy mr-0.5"></i> 复制
            </button>
          </div>
        </div>
      `).join('');

      // 绑定复制事件
      document.querySelectorAll('.copy-btn').forEach(btn => {
        btn.addEventListener('click', () => {
          const id = parseInt(btn.dataset.id);
          const content = blessings.find(b => b.id === id).content;
          if (content === '无') return showToast('无内容');
          navigator.clipboard.writeText(content).then(() => showToast());
        });
      });
    }

    
    // 初始化渲染
    document.addEventListener('DOMContentLoaded', renderBlessings);

    // 提示框
    function showToast(msg = '已复制') {
      const toast = document.getElementById('toast');
      toast.querySelector('span').textContent = msg;
      toast.classList.add('opacity-100');
      setTimeout(() => toast.classList.remove('opacity-100'), 1500);
    }
  </script>

    
