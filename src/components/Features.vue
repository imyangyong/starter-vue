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
    ],
  },
]
</script>

<template>
  <Table class="mx-auto w-[800px]">
    <TableCaption>A list of Features.</TableCaption>
    <TableHeader>
      <TableRow class="font-medium">
        <TableHead>
          分类
        </TableHead>
        <TableHead>
          项目
        </TableHead>
      </TableRow>
    </TableHeader>
    <TableBody>
      <TableRow v-for="feature in features" :key="feature.title">
        <TableCell text-left>
          {{ feature.title }}
        </TableCell>
        <TableCell text-left>
          <Badge
            v-for="child in feature.children" :key="child.title"
            mr-2
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
