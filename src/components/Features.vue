<script setup lang="ts">
const features = [
  {
    title: '代码规范',
    description: '',
    children: [
      {
        title: 'ESLint',
        icon: 'i-carbon-ibm-watsonx-code-assistant-for-z-validation-assistant',
        link: '/eslint',
        description: '',
      },
    ],
  },
  {
    title: 'CICD',
    children: [
      {
        title: 'git hook(danger)',
        icon: 'i-carbon-traffic-incident',
        link: 'https://github.com/danger/danger-js',
      },
    ],
  },
  {
    title: 'CSS 规范',
    children: [
      {
        title: '原子化Css(Unocss)',
        icon: 'i-carbon-use-case-usage',
        link: 'https://unocss.dev/',
        description: '',
      },
      {
        title: 'Css in js(vanilla-extract)',
        icon: 'i-carbon-ibm-watsonx-code-assistant',
        link: 'https://vanilla-extract.style/',
        description: '',
      },
    ],
  },
  {
    title: '工具库',
    children: [
      {
        title: '时间日期(dayjs)',
        icon: 'i-carbon-calendar-heat-map',
        link: 'https://day.js.org/zh-CN/',
      },
      {
        title: '数字计算(big.js)',
        icon: 'i-carbon-calculator',
        link: '/number',
      },
      {
        title: '匹配库(micromatch)',
        icon: 'i-carbon-fish-multiple',
        link: 'https://github.com/micromatch/micromatch',
      },
      {
        title: '国际化(vue-i18n)',
        icon: 'i-carbon-translate',
        link: 'https://vue-i18n.intlify.dev/',
      },
      {
        title: '不可改变数据(immer)',
        icon: 'i-carbon-ibm-cloud-pak-manta-automated-data-lineage',
        link: 'https://github.com/immerjs/immer',
      },
    ],
  },
  {
    title: '动画',
    children: [
      {
        title: 'animation',
        icon: 'container-image-push-pull',
        link: 'https://github.com/greensock/GSAP',
      },
    ],
  },
  {
    title: '开发工具库',
    children: [
      {
        title: 'DOM 元素类型推断(typed-query-selector)',
        icon: 'i-carbon-document-signed',
        link: 'https://github.com/g-plane/typed-query-selector',
      },
    ],
  },
]
</script>

<template>
  <Table class="mx-auto w-[800px]">
    <TableCaption>A list of Features.</TableCaption>
    <TableHeader>
      <TableRow class="font-medium">
        <TableHead w-30>
          分类
        </TableHead>
        <TableHead>
          项目
        </TableHead>
      </TableRow>
    </TableHeader>
    <TableBody>
      <TableRow v-for="feature in features" :key="feature.title">
        <TableCell w-30 text-left>
          {{ feature.title }} <Button>Click me</Button>
        </TableCell>
        <TableCell text-left>
          <Badge
            v-for="child in feature.children" :key="child.title"
            mb-2 mr-2
          >
            <a v-if="child.link.startsWith('http')" :href="child.link" target="_blank">
              <div :class="child.icon" inline-block items-center align-sub />
              {{ child.title }}
            </a>
            <RouterLink v-else :to="child.link">
              <div :class="child.icon" inline-block items-center align-sub />
              {{ child.title }}
            </RouterLink>
          </Badge>
        </TableCell>
      </TableRow>
    </TableBody>
  </Table>
</template>
