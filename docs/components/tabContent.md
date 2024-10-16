---
title: TabContent 内容切换
---

# TabContent 内容切换

切换需要展示的内容。一般与标签切换共同使用。

### 基础用法

最基础的用法。与tab-bar配合使用。

<div class="m-demo-row">
    <div class="fence">
        <zrx-tab-bar v-model="tab1.current" :tabs="tab1.menu"></zrx-tab-bar>
        <zrx-tab-content :value="tab1.current">
            <span class="m-text" v-for="n in tab1.menu" :key="n.value">{{ n.label }}</span>
        </zrx-tab-content>
    </div>
</div>

::: tip
每个展示容器都需设置属性"key"，与组件value相同的key对应的展示容器会被显示。
:::

::: details 示例代码

```html
<zrx-tab-bar v-model="tab1.current" :tabs="tab1.menu"></zrx-tab-bar>
<zrx-tab-content :value="tab1.current">
    <span class="m-text" v-for="n in tab1.menu" :key="n.value">{{ n.label }}</span>
</zrx-tab-content>
<script>
export default {
    data() {
        return {
            tab1: {
                current: '1',
                menu: [
                    {
                        label: '应用中心',
                        value: '1'
                    },
                    {
                        label: '用户中心',
                        value: '2'
                    },
                    {
                        label: '应用管理',
                        value: '3'
                    }
                ]
            }
        }
    }
}
</script>
```

:::

### 模式切换

<div class="m-demo-row">
    <p class="m-row">
        选择切换模式：
        <el-select v-model="tab4.mode">
            <el-option value="scroll"></el-option>
            <el-option value="v-if"></el-option>
            <el-option value="v-show"></el-option>
        </el-select>
    </p>
    <div class="fence">
        <zrx-tab-bar v-model="tab4.current" :tabs="tab4.tabs"></zrx-tab-bar>
        <zrx-tab-content :value="tab4.current" :shift-mode="tab4.mode">
            <div class="m-text" v-for="n in tab4.tabs" :key="n.value">
                <b>{{ n.label }}</b>
            </div>
        </zrx-tab-content>
    </div>
</div>

::: tip
tab-content内置了3种切换模式：scroll, v-if, v-show。 分别对应内容的三种渲染形式：全部渲染并展示, 只渲染当前项的，渲染所有但只展示当前项。
:::

::: details 示例代码

```html
选择切换模式：
<el-select v-model="tab4.mode">
    <el-option value="scroll"></el-option>
    <el-option value="v-if"></el-option>
    <el-option value="v-show"></el-option>
</el-select>
<zrx-tab-bar v-model="tab4.current" :tabs="tab4.tabs"></zrx-tab-bar>
<zrx-tab-content :value="tab4.current" :shift-mode="tab4.mode">
    <div class="m-text" v-for="n in tab4.tabs" :key="n.value">
        <b>{{ n.label }}</b>
    </div>
</zrx-tab-content>
<script>
export default {
    data() {
        return {
            tab4: {
                current: 1,
                mode: 'scroll',
                tabs: [
                    {
                        label: '工商银行',
                        value: 1
                    },
                    {
                        label: '农业银行',
                        value: 2
                    },
                    {
                        label: '建设银行',
                        value: 3
                    },
                    {
                        label: '中国银行',
                        value: 4
                    }
                ]
            }
        }
    }
}
</script>
```

:::

### 过渡效果

改变切换时的过渡效果

<div class="m-demo-row">
    <p class="m-row">
        选择过渡效果：
        <el-select v-model="tab5.mode">
            <el-option value="slide"></el-option>
            <el-option value="fade"></el-option>
            <el-option label="自定义类名zoomInOut" value="zoomInOut"></el-option>
            <el-option label="无" :value="false"></el-option>
        </el-select>
    </p>
    <div class="fence">
        <zrx-tab-bar v-model="tab5.current" :tabs="tab5.tabs"></zrx-tab-bar>
        <zrx-tab-content :value="tab5.current" :transition-type="tab5.mode" shift-mode="v-if" style="height: 54px">
            <div class="m-text" v-for="n in tab5.tabs" :key="n.value">{{ n.label }}</div>
        </zrx-tab-content>
    </div>
</div>

::: tip
v-if、v-show切换模式基于内置vue transition标签，可传入过渡动效，包括内置的"slide"、"fade"，或者自定义的过渡类名。当传入""或false时不进行过渡。
:::

::: details 示例代码

```html
选择过渡效果：
<el-select v-model="tab5.mode">
    <el-option value="slide"></el-option>
    <el-option value="fade"></el-option>
    <el-option label="自定义类名zoomInOut" value="zoomInOut"></el-option>
    <el-option label="无" :value="false"></el-option>
</el-select>
<zrx-tab-bar v-model="tab5.current" :tabs="tab5.tabs"></zrx-tab-bar>
<zrx-tab-content :value="tab5.current" :transition-type="tab5.mode" shift-mode="v-if">
    <div class="m-text" v-for="n in tab5.tabs" :key="n.value">{{ n.label }}</div>
</zrx-tab-content>
<script>
export default {
    data() {
        return {
            tab5: {
                current: '公积金',
                mode: 'slide',
                tabs: [
                    {
                        label: '公积金',
                        value: '公积金'
                    },
                    {
                        label: '社保',
                        value: '社保'
                    },
                    {
                        label: '医保',
                        value: '医保'
                    }
                ]
            }
        }
    }
}
</script>
```

:::

### 竖向填充

占满页面剩余的高度

<div class="m-demo-row" style="padding-bottom: 0;">
    <div class="fence stretch">
        <zrx-tab-bar v-model="tab2.current" :tabs="tab2.menu"></zrx-tab-bar>
        <zrx-tab-content :value="tab2.current" stretch>
            <div class="table-box" key="1">
                <el-table header-row-class-name="header-row-class" :data="table1" row-key="id">
                    <el-table-column prop="category" label="名称" show-overflow-tooltip></el-table-column>
                    <el-table-column prop="value" label="值（亿元）" show-overflow-tooltip></el-table-column>
                    <el-table-column prop="sameYear" label="同比" show-overflow-tooltip></el-table-column>
                    <el-table-column prop="sequential" label="环比" show-overflow-tooltip></el-table-column>
                </el-table>
                <zrx-pagination
                    layout="total, sizes, ->, prev, pager, next, jumper"
                    :page-size="10"
                    :current-page="1"
                    :page-sizes="[10, 20, 40, 80]"
                    :total="3"
                    :pagerCount="10"
                    :smallWidth="1280"
                    adaptiveWidth
                    background
                ></zrx-pagination>
            </div>
            <div class="table-box" key="2">
                <el-table header-row-class-name="header-row-class" :data="table2" row-key="id">
                    <el-table-column prop="category" label="名称" show-overflow-tooltip></el-table-column>
                    <el-table-column prop="value" label="值（亿元）" show-overflow-tooltip></el-table-column>
                    <el-table-column prop="sameYear" label="同比" show-overflow-tooltip></el-table-column>
                    <el-table-column prop="sequential" label="环比" show-overflow-tooltip></el-table-column>
                </el-table>
                <zrx-pagination
                    layout="total, sizes, ->, prev, pager, next, jumper"
                    :page-size="10"
                    :current-page="1"
                    :page-sizes="[10, 20, 40, 80]"
                    :total="3"
                    :pagerCount="10"
                    :smallWidth="1280"
                    adaptiveWidth
                    background
                ></zrx-pagination>
            </div>
        </zrx-tab-content>
    </div>
</div>

::: tip
tab-content若设置了高度，内容元素默认占100%高度。若tab-content高度不确定，可设置内容自动占满高度。
:::

::: details 示例代码

```html
<zrx-tab-bar v-model="tab2.current" :tabs="tab2.menu"></zrx-tab-bar>
<zrx-tab-content :value="tab2.current" stretch>
    <div class="table-box" key="1">
        <el-table header-row-class-name="header-row-class" :data="table1" row-key="id">
            <el-table-column prop="category" label="名称" show-overflow-tooltip></el-table-column>
            <el-table-column prop="value" label="值（亿元）" show-overflow-tooltip></el-table-column>
            <el-table-column prop="sameYear" label="同比" show-overflow-tooltip></el-table-column>
            <el-table-column prop="sequential" label="环比" show-overflow-tooltip></el-table-column>
        </el-table>
        <zrx-pagination
            layout="total, sizes, ->, prev, pager, next, jumper"
            :page-size="10"
            :current-page="1"
            :page-sizes="[10, 20, 40, 80]"
            :total="3"
            :pagerCount="10"
            :smallWidth="1280"
            adaptiveWidth
            background
        ></zrx-pagination>
    </div>
    <div class="table-box" key="2">
        <el-table header-row-class-name="header-row-class" :data="table2" row-key="id">
            <el-table-column prop="category" label="名称" show-overflow-tooltip></el-table-column>
            <el-table-column prop="value" label="值（亿元）" show-overflow-tooltip></el-table-column>
            <el-table-column prop="sameYear" label="同比" show-overflow-tooltip></el-table-column>
            <el-table-column prop="sequential" label="环比" show-overflow-tooltip></el-table-column>
        </el-table>
        <zrx-pagination
            layout="total, sizes, ->, prev, pager, next, jumper"
            :page-size="10"
            :current-page="1"
            :page-sizes="[10, 20, 40, 80]"
            :total="3"
            :pagerCount="10"
            :smallWidth="1280"
            adaptiveWidth
            background
        ></zrx-pagination>
    </div>
</zrx-tab-content>
<script>
export default {
    data() {
        return {
            tab2: {
                current: '1',
                menu: [
                    {
                        label: '一季度',
                        value: '1'
                    },
                    {
                        label: '二季度',
                        value: '2'
                    }
                ]
            }
        }
    }
}
</script>
```

:::

### 手动初始化

<div class="m-demo-row">
    <p class="m-row"><el-button type="primary" @click="init">加载数据</el-button></p>
    <div class="fence">
        <zrx-tab-bar v-model="tab3.current" :tabs="tab3.menu"></zrx-tab-bar>
        <zrx-tab-content :value="tab3.current" ref="tabContent">
            <span class="m-text" v-for="(n, i) in data1" :key="tab3.menu[i].value">{{ n }} </span>
        </zrx-tab-content>
        <zrx-empty-state v-if="!data1.length"></zrx-empty-state>
    </div>
</div>

::: tip
有些场景下，tab-content内容可能延迟渲染，或在第一次渲染后改变。组件对内容改变的监听基于MutationObserver。在某些情况下，MutationObserver可能不会触发，此时需在渲染后调用init方法。注意只有切换模式为scroll的才需要该步骤。
:::

::: details 示例代码

```html
<el-button type="primary" @click="init">加载数据</el-button>
<zrx-tab-bar v-model="tab3.current" :tabs="tab3.menu"></zrx-tab-bar>
<zrx-tab-content :value="tab3.current" ref="tabContent">
    <span class="m-text" v-for="(n, i) in data1" :key="tab3.menu[i].value">{{ n }} </span>
</zrx-tab-content>
<zrx-empty-state v-if="!data1.length"></zrx-empty-state>
<script>
export default {
    data() {
        return {
            tab3: {
                current: '1',
                menu: [
                    {
                        label: '水晶糕',
                        value: '1'
                    },
                    {
                        label: '小笼包',
                        value: '2'
                    },
                    {
                        label: '豆沙糕',
                        value: '3'
                    }
                ]
            }
        }
    },
    methods: {
        init() {
            this.data1 = ['水晶糕', '小笼包', '豆沙糕']
            this.$nextTick(this.$refs.tabContent.init)
        }
    }
}
</script>
```

:::

### Attributes

| 参数              | 说明                              | 类型            | 可选值                             | 默认值 |
| ----------------- | --------------------------------- | --------------- | ---------------------------------- | ------ |
| `value`           | 展示项绑定值                      | string, number  | —                                  | —      |
| `stretch`         | 展示内容是否自动撑开              | boolean         | —                                  | false  |
| `shift-mode`      | 切换形式                          | string          | scroll, v-if, v-show               | scroll |
| `transition-type` | 过渡类型，shiftMode非scroll时生效 | string, boolean | slide, fade, 自定义类名, false, '' | slide  |
| `transition-tag`  | 即`transition-group-tag`          | string          | HTML Tags                          | div    |

### Methods

| 方法名称 | 说明   | 参数 |
| -------- | ------ | ---- |
| `init`   | 初始化 | —    |

### Slots

| 插槽名称 | 说明                 |
| -------- | -------------------- |
| —        | tab-content 内嵌内容 |

<div>
    <contributor :maintainer="['agua']" :members="['agua']"></contributor>
</div>

<script>
export default {
    data() {
        return {
            tab1: {
                current: '1',
                menu: [
                    {
                        label: '应用中心',
                        value: '1'
                    },
                    {
                        label: '用户中心',
                        value: '2'
                    },
                    {
                        label: '应用管理',
                        value: '3'
                    }
                ]
            },
            tab2: {
                current: '1',
                menu: [
                    {
                        label: '一季度',
                        value: '1'
                    },
                    {
                        label: '二季度',
                        value: '2'
                    }
                ]
            },
            tab3: {
                current: '1',
                menu: [
                    {
                        label: '水晶糕',
                        value: '1'
                    },
                    {
                        label: '小笼包',
                        value: '2'
                    },
                    {
                        label: '豆沙糕',
                        value: '3'
                    }
                ]
            },
            tab4: {
                current: 1,
                mode: 'scroll',
                tabs: [
                    {
                        label: '工商银行',
                        value: 1
                    },
                    {
                        label: '农业银行',
                        value: 2
                    },
                    {
                        label: '建设银行',
                        value: 3
                    },
                    {
                        label: '中国银行',
                        value: 4
                    }
                ]
            },
            tab5: {
                current: '公积金',
                mode: 'slide',
                tabs: [
                    {
                        label: '公积金',
                        value: '公积金'
                    },
                    {
                        label: '社保',
                        value: '社保'
                    },
                    {
                        label: '医保',
                        value: '医保'
                    }
                ]
            },
            table1: [
                {
                    id: '1',
                    category: '第一产业',
                    value: 33625.14,
                    sameYear: '8.14%',
                    sequential: '2.41%'
                },
                {
                    id: '2',
                    category: '第二产业',
                    value: 156940.3,
                    sameYear: '5.9%',
                    sequential: '4.38%'
                },
                {
                    id: '3',
                    category: '第三产业',
                    value: 223066.55,
                    sameYear: '2.33%',
                    sequential: '1.23%'
                }
            ],
            table2: [
                {
                    id: '1',
                    category: '第一产业',
                    value: 40155.33,
                    sameYear: '7.02%',
                    sequential: '3.26%'
                },
                {
                    id: '2',
                    category: '第二产业',
                    value: 178526.11,
                    sameYear: '6.13%',
                    sequential: '3.46%'
                },
                {
                    id: '3',
                    category: '第三产业',
                    value: 245892.78,
                    sameYear: '3.52%',
                    sequential: '2.86%'
                }
            ],
            data1: []
        }
    },
    methods: {
        init() {
            this.data1 = ['水晶糕', '小笼包', '豆沙糕']
            this.$nextTick(this.$refs.tabContent.init)
        }
    }
}
</script>

<style lang="scss" scoped>
.stretch {
    display: flex;
    flex-direction: column;
    height: 480px;
    .zrx-tab-content {
        flex: 1 1 auto;
    }
    .table-box {
        display: flex;
        flex-direction: column;
        .pagination {
            margin-top: auto;
        }
    }
}
.zoomInOut-enter,
.zoomInOut-leave-to {
    opacity: 0;
    transform: scale(0);
}
.zoomInOut-leave,
.zoomInOut-leave-active,
.zoomInOut-leave-to {
    display: none;
}
.zoomInOut-enter-active {
    transition: opacity 0.3s, transform 0.3s cubic-bezier(0.12, 0.4, 0.29, 1.46);
    transform-origin: 0 50%;
}
</style>
