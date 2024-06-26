<template>
  <div class="left-div">
    <ul id="line">
      <li v-for="(event, index) in events" :key="index">
        <div v-if="index === 0" class="first-focus"></div>
        <div v-else class="focus"></div>
        <div :class="{'first-event-date': index === 0, 'event-date': index !== 0}">{{ event.date }}</div>
        <div :class="{'first-event-description': index === 0, 'event-description': index !== 0}" v-html="getDescriptionHtml(event.description)"></div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'TimelineComponent',
  data() {
    return {
      events: [
      { date: '2024-04-05', description: '弃用腾讯云COS并顺利完成了全站图床的迁移' },
      { date: '2024-03-30', description: '搭建了[101速查手册](https://memo.101jc.com/)，将紧扣规范梳理各类检测知识点' },
      { date: '2024-03-24', description: '搭建了[今日热点](https://hot.101jc.com/)' },
      { date: '2024-03-23', description: '搭建了[101储物间](https://pan.101jc.com/)，将用于收集整理各类资源' },
      { date: '2024-03-22', description: '1. 创建了公众号“101检测”<br>2. 在首页添加了公众号二维码' },
      { date: '2024-03-21', description: '调整了首页日志的样式' },
      { date: '2024-03-20', description: '1. 发布新文章<br>[学习记录：保温锚栓拉拔试验](https://blog.101jc.com/archives/1710934798662)<br>2. 添加了打字机动画<br>3. 更新了主页布局' },
      { date: '2024-03-19', description: '修复了无法正常显示访问量的Bug，添加了轮播文本' },
      { date: '2024-03-18', description: '1. 发布新文章<br>[学习记录：拉结筋、构造柱植筋拉拔试验](https://blog.101jc.com/archives/1710767324859)<br>2. 发布新文章<br>[学习记录：碳纤维布加固正拉粘结强度测试.](https://blog.101jc.com/archives/1710771385186)' },
      { date: '2024-03-17', description: '1. 添加了评论组件的评价功能，优化了评论样式<br>2. 发布新文章<br>[精读《公路桥梁荷载试验规程》：#02 桥梁索力测试](https://blog.101jc.com/archives/1710664500878)<br>3. 发布新文章<br>[学习记录：塑料管材性能试验方法](https://blog.101jc.com/archives/1710675384029)' },
      { date: '2024-03-16', description: '优化了桌面端和移动端的页脚组件布局及样式，添加了访问量及运行天数统计' },
      { date: '2024-03-15', description: '优化了评论组件的样式，开启了评论审核功能' },
      { date: '2024-03-14', description: '更新了首页日志的样式，点击链接可跳转到对应站点或文章' },
      { date: '2024-03-13', description: '搭建了[时光相册](https://pic.101jc.com/)' },
      { date: '2024-03-12', description: '修改了首页日志的样式，突出显示了最新的日志记录' },
      { date: '2024-03-11', description: '添加了主页留言板功能，添加了微信二维码及留言板按钮' },
      { date: '2024-03-10', description: '制作了动态头像并更新了主页布局' },
      { date: '2024-03-09', description: '搭建[IT工具箱](https://tool.101jc.com/)' },
      { date: '2024-03-08', description: '搭建[站点监测](https://site.101jc.com/)' },
        { date: '2024-03-07', description: '搭建[更新日志](https://log.101jc.com/)' },
        { date: '2024-03-06', description: '搭建[101知识库](https://lib.101jc.com/)' },
        { date: '2024-03-05', description: '学习Github并搭建[个人主页](https://101jc.com/)' },
        { date: '2024-01-29', description: '发布文章数量达到10篇' },
        { date: '2024-01-23', description: '利用腾讯云COS及Edgeone自建图床' },
        { date: '2024-01-12', description: '使用Halo框架及Hao主题搭建[博客](https://blog.101jc.com/)' },
        { date: '2023-11-18', description: '公安备案通过' },
        { date: '2023-11-13', description: '公安备案被拒并再次提交' },
        { date: '2023-11-10', description: '首次提交公安备案' },
        { date: '2023-10-30', description: '主体申请通过' },
        { date: '2023-10-24', description: '首次提交主体申请' },
        { date: '2023-10-23', description: 'ICP备案通过' },
        { date: '2023-10-14', description: '第二个域名提交ICP备案' },
        { date: '2023-10-13', description: '购买第二个域名101jc.com' },
        { date: '2023-05-17', description: '首个域名ICP备案通过' },
        { date: '2023-05-10', description: '首次提交ICP备案' },
        { date: '2023-05-08', description: '购买第一个域名jcgjx.cn' },
        { date: '2023-05-08', description: '购买第一台云服务器' },
      ],
    };
  },
  methods: {
  getDescriptionHtml(description) {
    // 正则表达式匹配Markdown风格的链接
    const regex = /\[([^\]]+)\]\((https?:\/\/[^\s]+)\)/g;
    let html = description.replace(regex, '<a href="$2" target="_blank" style="color: #555555;text-decoration: none; cursor: pointer !important;" class="custom-link" onmouseover="this.style.color=\'#00ffff\'; this.style.textDecoration=\'underline\'" onmouseout="this.style.color=\'#000000\'; this.style.textDecoration=\'none\'">$1</a>');
    // 将<br>标签转换为换行
    html = html.replace(/<br>/g, '</br>');
    return html;
  },
},
};
</script>



<style scoped>
.left-div {
  flex-shrink: 0;
  width: 90%;
  height: 100%;
  border-radius: 13px;
  padding: 0px;
  backdrop-filter: 0px;

}
#line {
    width: 100%;
    height: 220px;
    font-size: 14px;
    scroll-snap-type: y mandatory;
    overflow-y: scroll;
    /* 隐藏滚动条，但仍然允许滚动 */
    -ms-overflow-style: none;  /* Internet Explorer和Edge */
    scrollbar-width: none;  /* Firefox */
    overflow: -moz-scrollbars-none; /* 旧的Mozilla浏览器 */
}

@media (max-width: 768px) {
    #line {
        height: 140px; /* 移动端高度调整为120px */
    }
}
#line::-webkit-scrollbar {
    display: none; /* 对于基于Webkit的浏览器，如Chrome、Safari等 */
}

#line li {
    list-style: none;
    position: relative;
    padding: 15px 0px 0px 15px;
    border-left: 2px solid #fff;
    border-radius: 0;
    scroll-snap-align: end;
    color: var(--main-text-color);
}
#line li:first-child .focus:first-child {
    background-color: #aaffcd;
    animation: colorFlash 1s ease infinite;
}
.first-event-date {
  color: #ffffff; /* 第一个事件的日期颜色 */
}
.event-date {
  color: #fff; /* 其他事件的日期颜色 */
}
.first-event-description {
  color: #ffffff; /* 第一个事件的描述颜色 */
}
.event-description {
  color: #fff; /* 其他事件的描述颜色 */
}

@keyframes colorFlash {
  0% { background-color: #aaffcd; }
  50% { background-color: #00FDA1; }
  100% { background-color: #aaffcd; }
}
.first-focus {
    width: 17px;
    height: 2px;
    background-color: #fff;
    position: absolute;
    left: -9px;
    top: 23px;
    
}

.focus {
    width: 15px;
    height: 2px;
    background-color: #FFF;
    position: absolute;
    left: -9px;
    top: 23px;
    
}

</style>
