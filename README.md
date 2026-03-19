<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Show Page</title>
    <style>
        body {
            margin: 0;
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
            background: #121212;
            color: #e0e0e0;
            line-height: 1.8;
        }

        /* 核心布局：右图左文 + 整体垂直居中 */
        .layout {
            display: flex;
            flex-direction: row-reverse; /* 右图左文 */
            min-height: 90vh; /* 占满视口高度，居中更明显 */
            align-items: center; /* 👈 关键：子元素垂直居中（文本和图片对齐） */
            padding: 2rem;
            gap: 2rem; /* 👈 新增：文本和图片之间留间距，避免挤在一起 */
        }

        /* 图片容器 (right)：宽度自适应 */
        .layout .right {
            flex: 0 0 auto;
            display: flex;
            align-items: center; /* 图片在容器内居中 */
            justify-content: flex-end;
        }

        .layout .right img {
            max-width: 100%;
            max-height: 80vh; /* 限制图片高度，避免溢出 */
            object-fit: contain;
            width: auto;
            height: auto;
            border-radius: 12px;
            box-shadow: 0 8px 24px rgba(0,0,0,0.3);
            display: block;
        }

        /* 文字容器 (left)：垂直居中，占满剩余空间 */
        .layout .left {
            flex: 1;
            min-width: 300px;
            display: flex;
            flex-direction: column;
            justify-content: center; /* 👈 文字在容器内垂直居中 */
            position: relative;
            padding-left: 2rem; /* 避开左侧竖线 */
        }

        /* 左侧竖线：和文字容器等高 */
        .layout .left::before {
            content: "";
            position: absolute;
            left: 0;
            top: 0;
            height: 100%;
            width: 3px;
            background: #444;
            border-radius: 2px;
        }

        /* 标题样式：间距合理 */
        .layout .left h1 {
            font-size: 2rem;
            color: #fff;
            margin: 0 0 1.5rem 0;
            font-weight: 700;
        }

        /* 正文文本 */
        .quote-content {
            font-size: 1.25rem;
            color: #e0e0e0;
        }

        /* 出处：居右 */
        .quote-source {
            margin-left: auto;
            text-align: right;
            margin-top: 1.5rem;
            font-size: 1.1rem;
            color: #999;
        }

        /* 移动端适配 */
        @media (max-width: 768px) {
            .layout {
                flex-direction: column;
                gap: 1rem;
            }
            .layout .left {
                padding-left: 0;
            }
            .layout .left::before {
                display: none;
            }
        }
    </style>
</head>
<body>
    <div class="layout">
        <div class="right">
            <img src="image/hina.jpg" alt="展示图片" width="1200" height="900">
        </div>

        <div class="left">
            <h1>标题</h1>
            <div class="quote-content">
                我们凝望着最初的凝望，感到另一颗心跨越时空，望见生命的力量之和。<br>
                We gaze upon the first gaze,feeling another heart transcend time and space,<br>
                我们凝视着第一眼，感受到另一颗心超越了时间和空间。<br>
                seeing the sum of the power of life.<br>
                领悟生命的力量总和。<br>
                <div class="quote-source">
                    ———— 《National Treasure》 --"国宝"
                </div>
            </div>
        </div>
    </div>
</body>
</html>
