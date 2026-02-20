# 豆瓣评分聚合 / MultiRatingss

在豆瓣电影页面显示 IMDb、Letterboxd 和 Rotten Tomatoes 的评分信息。

## 功能特性

- 仅在豆瓣电影条目页（`*://movie.douban.com/subject/*`）生效，自动读取页面中的 IMDb 编号（如 `tt4968738`）。

- 在页面上展示 Letterboxd、IMDb 和 Rotten Tomatoes（含影评人与观众评分）评分。
- 恢复了豆瓣 IMDb 编号的链接功能，并附带 Letterboxd 与 Rotten Tomatoes 的跳转链接。

## 使用说明

1. 打开任意豆瓣电影条目页；
2. 页面加载完成后脚本将自动运行，此时您应该可以看到豆瓣评分的下面出现了 Letterboxd 评分；
3. 点击"展开更多"即可查看 IMDb 与 Rotten Tomatoes 评分。

## 数据获取逻辑

- **IMDb**：请求 `https://www.imdb.com/title/{imdbId}/` 并解析评分与投票人数。
- **Rotten Tomatoes**：先按英文标题搜索目标电影，进入命中页面后优先解析 `score-board` 元素，若失败则回退至 JSON 方式解析。
- **Letterboxd**：优先通过 IMDb ID 直达 `https://letterboxd.com/imdb/{imdbId}/`，未命中时回退至标题搜索。

## 配置声明

- `@grant GM_xmlhttpRequest`
- `@connect`
  - `www.imdb.com`
  - `www.rottentomatoes.com`
  - `letterboxd.com`

## 已知限制

- 解析逻辑依赖第三方网站的 DOM 结构，若对方页面改版可能导致解析失败。
- 当豆瓣条目缺少 IMDb 编号或英文标题时，Rotten Tomatoes 与 Letterboxd 可能无法正确匹配。

## 许可证

[The GNU General Public License v3.0
](https://www.gnu.org/licenses/gpl-3.0.html) © [**SuperLangdon**](https://langdon.one)

## 致谢

- MultiRatingss 脚本基于 [AirBashX](https://github.com/SuperLangdon/my-userscripts) 和 [Yan Yu](https://greasyfork.org/zh-CN/scripts/557914-%E8%B1%86%E7%93%A3%E5%8A%A9%E6%89%8B-%E8%87%AA%E7%94%A8%E4%BA%8C%E6%94%B9) 的代码修改。