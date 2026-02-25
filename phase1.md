---
layout: default
title: Phase 1 – Data Preprocessing
nav_order: 4
---


<div class="notebook">
    <html lang="en">
    <head><meta charset="utf-8"/>
    <meta content="width=device-width, initial-scale=1.0" name="viewport"/>
    <title>Assignment1_Cleaned</title><script src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.1.10/require.min.js"></script>
    <style type="text/css">
        pre { line-height: 125%; }
    td.linenos .normal { color: inherit; background-color: transparent; padding-left: 5px; padding-right: 5px; }
    span.linenos { color: inherit; background-color: transparent; padding-left: 5px; padding-right: 5px; }
    td.linenos .special { color: #000000; background-color: #ffffc0; padding-left: 5px; padding-right: 5px; }
    span.linenos.special { color: #000000; background-color: #ffffc0; padding-left: 5px; padding-right: 5px; }
    .highlight .hll { background-color: var(--jp-cell-editor-active-background) }
    .highlight { background: var(--jp-cell-editor-background); color: var(--jp-mirror-editor-variable-color) }
    .highlight .c { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment */
    .highlight .err { color: var(--jp-mirror-editor-error-color) } /* Error */
    .highlight .k { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword */
    .highlight .o { color: var(--jp-mirror-editor-operator-color); font-weight: bold } /* Operator */
    .highlight .p { color: var(--jp-mirror-editor-punctuation-color) } /* Punctuation */
    .highlight .ch { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Hashbang */
    .highlight .cm { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Multiline */
    .highlight .cp { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Preproc */
    .highlight .cpf { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.PreprocFile */
    .highlight .c1 { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Single */
    .highlight .cs { color: var(--jp-mirror-editor-comment-color); font-style: italic } /* Comment.Special */
    .highlight .kc { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Constant */
    .highlight .kd { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Declaration */
    .highlight .kn { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Namespace */
    .highlight .kp { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Pseudo */
    .highlight .kr { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Reserved */
    .highlight .kt { color: var(--jp-mirror-editor-keyword-color); font-weight: bold } /* Keyword.Type */
    .highlight .m { color: var(--jp-mirror-editor-number-color) } /* Literal.Number */
    .highlight .s { color: var(--jp-mirror-editor-string-color) } /* Literal.String */
    .highlight .ow { color: var(--jp-mirror-editor-operator-color); font-weight: bold } /* Operator.Word */
    .highlight .pm { color: var(--jp-mirror-editor-punctuation-color) } /* Punctuation.Marker */
    .highlight .w { color: var(--jp-mirror-editor-variable-color) } /* Text.Whitespace */
    .highlight .mb { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Bin */
    .highlight .mf { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Float */
    .highlight .mh { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Hex */
    .highlight .mi { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Integer */
    .highlight .mo { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Oct */
    .highlight .sa { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Affix */
    .highlight .sb { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Backtick */
    .highlight .sc { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Char */
    .highlight .dl { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Delimiter */
    .highlight .sd { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Doc */
    .highlight .s2 { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Double */
    .highlight .se { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Escape */
    .highlight .sh { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Heredoc */
    .highlight .si { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Interpol */
    .highlight .sx { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Other */
    .highlight .sr { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Regex */
    .highlight .s1 { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Single */
    .highlight .ss { color: var(--jp-mirror-editor-string-color) } /* Literal.String.Symbol */
    .highlight .il { color: var(--jp-mirror-editor-number-color) } /* Literal.Number.Integer.Long */
    </style>
    <style type="text/css">
    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    /*
    * Mozilla scrollbar styling
    */

    /* use standard opaque scrollbars for most nodes */
    [data-jp-theme-scrollbars='true'] {
    scrollbar-color: rgb(var(--jp-scrollbar-thumb-color))
        var(--jp-scrollbar-background-color);
    }

    /* for code nodes, use a transparent style of scrollbar. These selectors
    * will match lower in the tree, and so will override the above */
    [data-jp-theme-scrollbars='true'] .CodeMirror-hscrollbar,
    [data-jp-theme-scrollbars='true'] .CodeMirror-vscrollbar {
    scrollbar-color: rgba(var(--jp-scrollbar-thumb-color), 0.5) transparent;
    }

    /* tiny scrollbar */

    .jp-scrollbar-tiny {
    scrollbar-color: rgba(var(--jp-scrollbar-thumb-color), 0.5) transparent;
    scrollbar-width: thin;
    }

    /* tiny scrollbar */

    .jp-scrollbar-tiny::-webkit-scrollbar,
    .jp-scrollbar-tiny::-webkit-scrollbar-corner {
    background-color: transparent;
    height: 4px;
    width: 4px;
    }

    .jp-scrollbar-tiny::-webkit-scrollbar-thumb {
    background: rgba(var(--jp-scrollbar-thumb-color), 0.5);
    }

    .jp-scrollbar-tiny::-webkit-scrollbar-track:horizontal {
    border-left: 0 solid transparent;
    border-right: 0 solid transparent;
    }

    .jp-scrollbar-tiny::-webkit-scrollbar-track:vertical {
    border-top: 0 solid transparent;
    border-bottom: 0 solid transparent;
    }

    /*
    * Lumino
    */

    .lm-ScrollBar[data-orientation='horizontal'] {
    min-height: 16px;
    max-height: 16px;
    min-width: 45px;
    border-top: 1px solid #a0a0a0;
    }

    .lm-ScrollBar[data-orientation='vertical'] {
    min-width: 16px;
    max-width: 16px;
    min-height: 45px;
    border-left: 1px solid #a0a0a0;
    }

    .lm-ScrollBar-button {
    background-color: #f0f0f0;
    background-position: center center;
    min-height: 15px;
    max-height: 15px;
    min-width: 15px;
    max-width: 15px;
    }

    .lm-ScrollBar-button:hover {
    background-color: #dadada;
    }

    .lm-ScrollBar-button.lm-mod-active {
    background-color: #cdcdcd;
    }

    .lm-ScrollBar-track {
    background: #f0f0f0;
    }

    .lm-ScrollBar-thumb {
    background: #cdcdcd;
    }

    .lm-ScrollBar-thumb:hover {
    background: #bababa;
    }

    .lm-ScrollBar-thumb.lm-mod-active {
    background: #a0a0a0;
    }

    .lm-ScrollBar[data-orientation='horizontal'] .lm-ScrollBar-thumb {
    height: 100%;
    min-width: 15px;
    border-left: 1px solid #a0a0a0;
    border-right: 1px solid #a0a0a0;
    }

    .lm-ScrollBar[data-orientation='vertical'] .lm-ScrollBar-thumb {
    width: 100%;
    min-height: 15px;
    border-top: 1px solid #a0a0a0;
    border-bottom: 1px solid #a0a0a0;
    }

    .lm-ScrollBar[data-orientation='horizontal']
    .lm-ScrollBar-button[data-action='decrement'] {
    background-image: var(--jp-icon-caret-left);
    background-size: 17px;
    }

    .lm-ScrollBar[data-orientation='horizontal']
    .lm-ScrollBar-button[data-action='increment'] {
    background-image: var(--jp-icon-caret-right);
    background-size: 17px;
    }

    .lm-ScrollBar[data-orientation='vertical']
    .lm-ScrollBar-button[data-action='decrement'] {
    background-image: var(--jp-icon-caret-up);
    background-size: 17px;
    }

    .lm-ScrollBar[data-orientation='vertical']
    .lm-ScrollBar-button[data-action='increment'] {
    background-image: var(--jp-icon-caret-down);
    background-size: 17px;
    }

    /*
    * Copyright (c) Jupyter Development Team.
    * Distributed under the terms of the Modified BSD License.
    */

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Copyright (c) 2014-2017, PhosphorJS Contributors
    |
    | Distributed under the terms of the BSD 3-Clause License.
    |
    | The full license is in the file LICENSE, distributed with this software.
    |----------------------------------------------------------------------------*/

    .lm-Widget {
    box-sizing: border-box;
    position: relative;
    overflow: hidden;
    }

    .lm-Widget.lm-mod-hidden {
    display: none !important;
    }

    /*
    * Copyright (c) Jupyter Development Team.
    * Distributed under the terms of the Modified BSD License.
    */

    .lm-AccordionPanel[data-orientation='horizontal'] > .lm-AccordionPanel-title {
    /* Title is rotated for horizontal accordion panel using CSS */
    display: block;
    transform-origin: top left;
    transform: rotate(-90deg) translate(-100%);
    }

    /*
    * Copyright (c) Jupyter Development Team.
    * Distributed under the terms of the Modified BSD License.
    */

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Copyright (c) 2014-2017, PhosphorJS Contributors
    |
    | Distributed under the terms of the BSD 3-Clause License.
    |
    | The full license is in the file LICENSE, distributed with this software.
    |----------------------------------------------------------------------------*/

    .lm-CommandPalette {
    display: flex;
    flex-direction: column;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    }

    .lm-CommandPalette-search {
    flex: 0 0 auto;
    }

    .lm-CommandPalette-content {
    flex: 1 1 auto;
    margin: 0;
    padding: 0;
    min-height: 0;
    overflow: auto;
    list-style-type: none;
    }

    .lm-CommandPalette-header {
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
    }

    .lm-CommandPalette-item {
    display: flex;
    flex-direction: row;
    }

    .lm-CommandPalette-itemIcon {
    flex: 0 0 auto;
    }

    .lm-CommandPalette-itemContent {
    flex: 1 1 auto;
    overflow: hidden;
    }

    .lm-CommandPalette-itemShortcut {
    flex: 0 0 auto;
    }

    .lm-CommandPalette-itemLabel {
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
    }

    .lm-close-icon {
    border: 1px solid transparent;
    background-color: transparent;
    position: absolute;
    z-index: 1;
    right: 3%;
    top: 0;
    bottom: 0;
    margin: auto;
    padding: 7px 0;
    display: none;
    vertical-align: middle;
    outline: 0;
    cursor: pointer;
    }
    .lm-close-icon:after {
    content: 'X';
    display: block;
    width: 15px;
    height: 15px;
    text-align: center;
    color: #000;
    font-weight: normal;
    font-size: 12px;
    cursor: pointer;
    }

    /*
    * Copyright (c) Jupyter Development Team.
    * Distributed under the terms of the Modified BSD License.
    */

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Copyright (c) 2014-2017, PhosphorJS Contributors
    |
    | Distributed under the terms of the BSD 3-Clause License.
    |
    | The full license is in the file LICENSE, distributed with this software.
    |----------------------------------------------------------------------------*/

    .lm-DockPanel {
    z-index: 0;
    }

    .lm-DockPanel-widget {
    z-index: 0;
    }

    .lm-DockPanel-tabBar {
    z-index: 1;
    }

    .lm-DockPanel-handle {
    z-index: 2;
    }

    .lm-DockPanel-handle.lm-mod-hidden {
    display: none !important;
    }

    .lm-DockPanel-handle:after {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    content: '';
    }

    .lm-DockPanel-handle[data-orientation='horizontal'] {
    cursor: ew-resize;
    }

    .lm-DockPanel-handle[data-orientation='vertical'] {
    cursor: ns-resize;
    }

    .lm-DockPanel-handle[data-orientation='horizontal']:after {
    left: 50%;
    min-width: 8px;
    transform: translateX(-50%);
    }

    .lm-DockPanel-handle[data-orientation='vertical']:after {
    top: 50%;
    min-height: 8px;
    transform: translateY(-50%);
    }

    .lm-DockPanel-overlay {
    z-index: 3;
    box-sizing: border-box;
    pointer-events: none;
    }

    .lm-DockPanel-overlay.lm-mod-hidden {
    display: none !important;
    }

    /*
    * Copyright (c) Jupyter Development Team.
    * Distributed under the terms of the Modified BSD License.
    */

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Copyright (c) 2014-2017, PhosphorJS Contributors
    |
    | Distributed under the terms of the BSD 3-Clause License.
    |
    | The full license is in the file LICENSE, distributed with this software.
    |----------------------------------------------------------------------------*/

    .lm-Menu {
    z-index: 10000;
    position: absolute;
    white-space: nowrap;
    overflow-x: hidden;
    overflow-y: auto;
    outline: none;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    }

    .lm-Menu-content {
    margin: 0;
    padding: 0;
    display: table;
    list-style-type: none;
    }

    .lm-Menu-item {
    display: table-row;
    }

    .lm-Menu-item.lm-mod-hidden,
    .lm-Menu-item.lm-mod-collapsed {
    display: none !important;
    }

    .lm-Menu-itemIcon,
    .lm-Menu-itemSubmenuIcon {
    display: table-cell;
    text-align: center;
    }

    .lm-Menu-itemLabel {
    display: table-cell;
    text-align: left;
    }

    .lm-Menu-itemShortcut {
    display: table-cell;
    text-align: right;
    }

    /*
    * Copyright (c) Jupyter Development Team.
    * Distributed under the terms of the Modified BSD License.
    */

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Copyright (c) 2014-2017, PhosphorJS Contributors
    |
    | Distributed under the terms of the BSD 3-Clause License.
    |
    | The full license is in the file LICENSE, distributed with this software.
    |----------------------------------------------------------------------------*/

    .lm-MenuBar {
    outline: none;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    }

    .lm-MenuBar-content {
    margin: 0;
    padding: 0;
    display: flex;
    flex-direction: row;
    list-style-type: none;
    }

    .lm-MenuBar-item {
    box-sizing: border-box;
    }

    .lm-MenuBar-itemIcon,
    .lm-MenuBar-itemLabel {
    display: inline-block;
    }

    /*
    * Copyright (c) Jupyter Development Team.
    * Distributed under the terms of the Modified BSD License.
    */

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Copyright (c) 2014-2017, PhosphorJS Contributors
    |
    | Distributed under the terms of the BSD 3-Clause License.
    |
    | The full license is in the file LICENSE, distributed with this software.
    |----------------------------------------------------------------------------*/

    .lm-ScrollBar {
    display: flex;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    }

    .lm-ScrollBar[data-orientation='horizontal'] {
    flex-direction: row;
    }

    .lm-ScrollBar[data-orientation='vertical'] {
    flex-direction: column;
    }

    .lm-ScrollBar-button {
    box-sizing: border-box;
    flex: 0 0 auto;
    }

    .lm-ScrollBar-track {
    box-sizing: border-box;
    position: relative;
    overflow: hidden;
    flex: 1 1 auto;
    }

    .lm-ScrollBar-thumb {
    box-sizing: border-box;
    position: absolute;
    }

    /*
    * Copyright (c) Jupyter Development Team.
    * Distributed under the terms of the Modified BSD License.
    */

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Copyright (c) 2014-2017, PhosphorJS Contributors
    |
    | Distributed under the terms of the BSD 3-Clause License.
    |
    | The full license is in the file LICENSE, distributed with this software.
    |----------------------------------------------------------------------------*/

    .lm-SplitPanel-child {
    z-index: 0;
    }

    .lm-SplitPanel-handle {
    z-index: 1;
    }

    .lm-SplitPanel-handle.lm-mod-hidden {
    display: none !important;
    }

    .lm-SplitPanel-handle:after {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    content: '';
    }

    .lm-SplitPanel[data-orientation='horizontal'] > .lm-SplitPanel-handle {
    cursor: ew-resize;
    }

    .lm-SplitPanel[data-orientation='vertical'] > .lm-SplitPanel-handle {
    cursor: ns-resize;
    }

    .lm-SplitPanel[data-orientation='horizontal'] > .lm-SplitPanel-handle:after {
    left: 50%;
    min-width: 8px;
    transform: translateX(-50%);
    }

    .lm-SplitPanel[data-orientation='vertical'] > .lm-SplitPanel-handle:after {
    top: 50%;
    min-height: 8px;
    transform: translateY(-50%);
    }

    /*
    * Copyright (c) Jupyter Development Team.
    * Distributed under the terms of the Modified BSD License.
    */

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Copyright (c) 2014-2017, PhosphorJS Contributors
    |
    | Distributed under the terms of the BSD 3-Clause License.
    |
    | The full license is in the file LICENSE, distributed with this software.
    |----------------------------------------------------------------------------*/

    .lm-TabBar {
    display: flex;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    }

    .lm-TabBar[data-orientation='horizontal'] {
    flex-direction: row;
    align-items: flex-end;
    }

    .lm-TabBar[data-orientation='vertical'] {
    flex-direction: column;
    align-items: flex-end;
    }

    .lm-TabBar-content {
    margin: 0;
    padding: 0;
    display: flex;
    flex: 1 1 auto;
    list-style-type: none;
    }

    .lm-TabBar[data-orientation='horizontal'] > .lm-TabBar-content {
    flex-direction: row;
    }

    .lm-TabBar[data-orientation='vertical'] > .lm-TabBar-content {
    flex-direction: column;
    }

    .lm-TabBar-tab {
    display: flex;
    flex-direction: row;
    box-sizing: border-box;
    overflow: hidden;
    touch-action: none; /* Disable native Drag/Drop */
    }

    .lm-TabBar-tabIcon,
    .lm-TabBar-tabCloseIcon {
    flex: 0 0 auto;
    }

    .lm-TabBar-tabLabel {
    flex: 1 1 auto;
    overflow: hidden;
    white-space: nowrap;
    }

    .lm-TabBar-tabInput {
    user-select: all;
    width: 100%;
    box-sizing: border-box;
    }

    .lm-TabBar-tab.lm-mod-hidden {
    display: none !important;
    }

    .lm-TabBar-addButton.lm-mod-hidden {
    display: none !important;
    }

    .lm-TabBar.lm-mod-dragging .lm-TabBar-tab {
    position: relative;
    }

    .lm-TabBar.lm-mod-dragging[data-orientation='horizontal'] .lm-TabBar-tab {
    left: 0;
    transition: left 150ms ease;
    }

    .lm-TabBar.lm-mod-dragging[data-orientation='vertical'] .lm-TabBar-tab {
    top: 0;
    transition: top 150ms ease;
    }

    .lm-TabBar.lm-mod-dragging .lm-TabBar-tab.lm-mod-dragging {
    transition: none;
    }

    .lm-TabBar-tabLabel .lm-TabBar-tabInput {
    user-select: all;
    width: 100%;
    box-sizing: border-box;
    background: inherit;
    }

    /*
    * Copyright (c) Jupyter Development Team.
    * Distributed under the terms of the Modified BSD License.
    */

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Copyright (c) 2014-2017, PhosphorJS Contributors
    |
    | Distributed under the terms of the BSD 3-Clause License.
    |
    | The full license is in the file LICENSE, distributed with this software.
    |----------------------------------------------------------------------------*/

    .lm-TabPanel-tabBar {
    z-index: 1;
    }

    .lm-TabPanel-stackedPanel {
    z-index: 0;
    }

    /*
    * Copyright (c) Jupyter Development Team.
    * Distributed under the terms of the Modified BSD License.
    */

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Copyright (c) 2014-2017, PhosphorJS Contributors
    |
    | Distributed under the terms of the BSD 3-Clause License.
    |
    | The full license is in the file LICENSE, distributed with this software.
    |----------------------------------------------------------------------------*/

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    .jp-Collapse {
    display: flex;
    flex-direction: column;
    align-items: stretch;
    }

    .jp-Collapse-header {
    padding: 1px 12px;
    background-color: var(--jp-layout-color1);
    border-bottom: solid var(--jp-border-width) var(--jp-border-color2);
    color: var(--jp-ui-font-color1);
    cursor: pointer;
    display: flex;
    align-items: center;
    font-size: var(--jp-ui-font-size0);
    font-weight: 600;
    text-transform: uppercase;
    user-select: none;
    }

    .jp-Collapser-icon {
    height: 16px;
    }

    .jp-Collapse-header-collapsed .jp-Collapser-icon {
    transform: rotate(-90deg);
    margin: auto 0;
    }

    .jp-Collapser-title {
    line-height: 25px;
    }

    .jp-Collapse-contents {
    padding: 0 12px;
    background-color: var(--jp-layout-color1);
    color: var(--jp-ui-font-color1);
    overflow: auto;
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    /* This file was auto-generated by ensureUiComponents() in @jupyterlab/buildutils */

    /**
    * (DEPRECATED) Support for consuming icons as CSS background images
    */

    /* Icons urls */

    :root {
    --jp-icon-add-above: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTQiIGhlaWdodD0iMTQiIHZpZXdCb3g9IjAgMCAxNCAxNCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KPGcgY2xpcC1wYXRoPSJ1cmwoI2NsaXAwXzEzN18xOTQ5MikiPgo8cGF0aCBjbGFzcz0ianAtaWNvbjMiIGQ9Ik00Ljc1IDQuOTMwNjZINi42MjVWNi44MDU2NkM2LjYyNSA3LjAxMTkxIDYuNzkzNzUgNy4xODA2NiA3IDcuMTgwNjZDNy4yMDYyNSA3LjE4MDY2IDcuMzc1IDcuMDExOTEgNy4zNzUgNi44MDU2NlY0LjkzMDY2SDkuMjVDOS40NTYyNSA0LjkzMDY2IDkuNjI1IDQuNzYxOTEgOS42MjUgNC41NTU2NkM5LjYyNSA0LjM0OTQxIDkuNDU2MjUgNC4xODA2NiA5LjI1IDQuMTgwNjZINy4zNzVWMi4zMDU2NkM3LjM3NSAyLjA5OTQxIDcuMjA2MjUgMS45MzA2NiA3IDEuOTMwNjZDNi43OTM3NSAxLjkzMDY2IDYuNjI1IDIuMDk5NDEgNi42MjUgMi4zMDU2NlY0LjE4MDY2SDQuNzVDNC41NDM3NSA0LjE4MDY2IDQuMzc1IDQuMzQ5NDEgNC4zNzUgNC41NTU2NkM0LjM3NSA0Ljc2MTkxIDQuNTQzNzUgNC45MzA2NiA0Ljc1IDQuOTMwNjZaIiBmaWxsPSIjNjE2MTYxIiBzdHJva2U9IiM2MTYxNjEiIHN0cm9rZS13aWR0aD0iMC43Ii8+CjwvZz4KPHBhdGggY2xhc3M9ImpwLWljb24zIiBmaWxsLXJ1bGU9ImV2ZW5vZGQiIGNsaXAtcnVsZT0iZXZlbm9kZCIgZD0iTTExLjUgOS41VjExLjVMMi41IDExLjVWOS41TDExLjUgOS41Wk0xMiA4QzEyLjU1MjMgOCAxMyA4LjQ0NzcyIDEzIDlWMTJDMTMgMTIuNTUyMyAxMi41NTIzIDEzIDEyIDEzTDIgMTNDMS40NDc3MiAxMyAxIDEyLjU1MjMgMSAxMlY5QzEgOC40NDc3MiAxLjQ0NzcxIDggMiA4TDEyIDhaIiBmaWxsPSIjNjE2MTYxIi8+CjxkZWZzPgo8Y2xpcFBhdGggaWQ9ImNsaXAwXzEzN18xOTQ5MiI+CjxyZWN0IGNsYXNzPSJqcC1pY29uMyIgd2lkdGg9IjYiIGhlaWdodD0iNiIgZmlsbD0id2hpdGUiIHRyYW5zZm9ybT0ibWF0cml4KC0xIDAgMCAxIDEwIDEuNTU1NjYpIi8+CjwvY2xpcFBhdGg+CjwvZGVmcz4KPC9zdmc+Cg==);
    --jp-icon-add-below: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTQiIGhlaWdodD0iMTQiIHZpZXdCb3g9IjAgMCAxNCAxNCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KPGcgY2xpcC1wYXRoPSJ1cmwoI2NsaXAwXzEzN18xOTQ5OCkiPgo8cGF0aCBjbGFzcz0ianAtaWNvbjMiIGQ9Ik05LjI1IDEwLjA2OTNMNy4zNzUgMTAuMDY5M0w3LjM3NSA4LjE5NDM0QzcuMzc1IDcuOTg4MDkgNy4yMDYyNSA3LjgxOTM0IDcgNy44MTkzNEM2Ljc5Mzc1IDcuODE5MzQgNi42MjUgNy45ODgwOSA2LjYyNSA4LjE5NDM0TDYuNjI1IDEwLjA2OTNMNC43NSAxMC4wNjkzQzQuNTQzNzUgMTAuMDY5MyA0LjM3NSAxMC4yMzgxIDQuMzc1IDEwLjQ0NDNDNC4zNzUgMTAuNjUwNiA0LjU0Mzc1IDEwLjgxOTMgNC43NSAxMC44MTkzTDYuNjI1IDEwLjgxOTNMNi42MjUgMTIuNjk0M0M2LjYyNSAxMi45MDA2IDYuNzkzNzUgMTMuMDY5MyA3IDEzLjA2OTNDNy4yMDYyNSAxMy4wNjkzIDcuMzc1IDEyLjkwMDYgNy4zNzUgMTIuNjk0M0w3LjM3NSAxMC44MTkzTDkuMjUgMTAuODE5M0M5LjQ1NjI1IDEwLjgxOTMgOS42MjUgMTAuNjUwNiA5LjYyNSAxMC40NDQzQzkuNjI1IDEwLjIzODEgOS40NTYyNSAxMC4wNjkzIDkuMjUgMTAuMDY5M1oiIGZpbGw9IiM2MTYxNjEiIHN0cm9rZT0iIzYxNjE2MSIgc3Ryb2tlLXdpZHRoPSIwLjciLz4KPC9nPgo8cGF0aCBjbGFzcz0ianAtaWNvbjMiIGZpbGwtcnVsZT0iZXZlbm9kZCIgY2xpcC1ydWxlPSJldmVub2RkIiBkPSJNMi41IDUuNUwyLjUgMy41TDExLjUgMy41TDExLjUgNS41TDIuNSA1LjVaTTIgN0MxLjQ0NzcyIDcgMSA2LjU1MjI4IDEgNkwxIDNDMSAyLjQ0NzcyIDEuNDQ3NzIgMiAyIDJMMTIgMkMxMi41NTIzIDIgMTMgMi40NDc3MiAxMyAzTDEzIDZDMTMgNi41NTIyOSAxMi41NTIzIDcgMTIgN0wyIDdaIiBmaWxsPSIjNjE2MTYxIi8+CjxkZWZzPgo8Y2xpcFBhdGggaWQ9ImNsaXAwXzEzN18xOTQ5OCI+CjxyZWN0IGNsYXNzPSJqcC1pY29uMyIgd2lkdGg9IjYiIGhlaWdodD0iNiIgZmlsbD0id2hpdGUiIHRyYW5zZm9ybT0ibWF0cml4KDEgMS43NDg0NmUtMDcgMS43NDg0NmUtMDcgLTEgNCAxMy40NDQzKSIvPgo8L2NsaXBQYXRoPgo8L2RlZnM+Cjwvc3ZnPgo=);
    --jp-icon-add: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE5IDEzaC02djZoLTJ2LTZINXYtMmg2VjVoMnY2aDZ2MnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-bell: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE2IDE2IiB2ZXJzaW9uPSIxLjEiPgogICA8cGF0aCBjbGFzcz0ianAtaWNvbjIganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjMzMzMzMzIgogICAgICBkPSJtOCAwLjI5Yy0xLjQgMC0yLjcgMC43My0zLjYgMS44LTEuMiAxLjUtMS40IDMuNC0xLjUgNS4yLTAuMTggMi4yLTAuNDQgNC0yLjMgNS4zbDAuMjggMS4zaDVjMC4wMjYgMC42NiAwLjMyIDEuMSAwLjcxIDEuNSAwLjg0IDAuNjEgMiAwLjYxIDIuOCAwIDAuNTItMC40IDAuNi0xIDAuNzEtMS41aDVsMC4yOC0xLjNjLTEuOS0wLjk3LTIuMi0zLjMtMi4zLTUuMy0wLjEzLTEuOC0wLjI2LTMuNy0xLjUtNS4yLTAuODUtMS0yLjItMS44LTMuNi0xLjh6bTAgMS40YzAuODggMCAxLjkgMC41NSAyLjUgMS4zIDAuODggMS4xIDEuMSAyLjcgMS4yIDQuNCAwLjEzIDEuNyAwLjIzIDMuNiAxLjMgNS4yaC0xMGMxLjEtMS42IDEuMi0zLjQgMS4zLTUuMiAwLjEzLTEuNyAwLjMtMy4zIDEuMi00LjQgMC41OS0wLjcyIDEuNi0xLjMgMi41LTEuM3ptLTAuNzQgMTJoMS41Yy0wLjAwMTUgMC4yOCAwLjAxNSAwLjc5LTAuNzQgMC43OS0wLjczIDAuMDAxNi0wLjcyLTAuNTMtMC43NC0wLjc5eiIgLz4KPC9zdmc+Cg==);
    --jp-icon-bug-dot: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjQiIGhlaWdodD0iMjQiIHZpZXdCb3g9IjAgMCAyNCAyNCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiM2MTYxNjEiPgogICAgICAgIDxwYXRoIGZpbGwtcnVsZT0iZXZlbm9kZCIgY2xpcC1ydWxlPSJldmVub2RkIiBkPSJNMTcuMTkgOEgyMFYxMEgxNy45MUMxNy45NiAxMC4zMyAxOCAxMC42NiAxOCAxMVYxMkgyMFYxNEgxOC41SDE4VjE0LjAyNzVDMTUuNzUgMTQuMjc2MiAxNCAxNi4xODM3IDE0IDE4LjVDMTQgMTkuMjA4IDE0LjE2MzUgMTkuODc3OSAxNC40NTQ5IDIwLjQ3MzlDMTMuNzA2MyAyMC44MTE3IDEyLjg3NTcgMjEgMTIgMjFDOS43OCAyMSA3Ljg1IDE5Ljc5IDYuODEgMThINFYxNkg2LjA5QzYuMDQgMTUuNjcgNiAxNS4zNCA2IDE1VjE0SDRWMTJINlYxMUM2IDEwLjY2IDYuMDQgMTAuMzMgNi4wOSAxMEg0VjhINi44MUM3LjI2IDcuMjIgNy44OCA2LjU1IDguNjIgNi4wNEw3IDQuNDFMOC40MSAzTDEwLjU5IDUuMTdDMTEuMDQgNS4wNiAxMS41MSA1IDEyIDVDMTIuNDkgNSAxMi45NiA1LjA2IDEzLjQyIDUuMTdMMTUuNTkgM0wxNyA0LjQxTDE1LjM3IDYuMDRDMTYuMTIgNi41NSAxNi43NCA3LjIyIDE3LjE5IDhaTTEwIDE2SDE0VjE0SDEwVjE2Wk0xMCAxMkgxNFYxMEgxMFYxMloiIGZpbGw9IiM2MTYxNjEiLz4KICAgICAgICA8cGF0aCBkPSJNMjIgMTguNUMyMiAyMC40MzMgMjAuNDMzIDIyIDE4LjUgMjJDMTYuNTY3IDIyIDE1IDIwLjQzMyAxNSAxOC41QzE1IDE2LjU2NyAxNi41NjcgMTUgMTguNSAxNUMyMC40MzMgMTUgMjIgMTYuNTY3IDIyIDE4LjVaIiBmaWxsPSIjNjE2MTYxIi8+CiAgICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-bug: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxwYXRoIGQ9Ik0yMCA4aC0yLjgxYy0uNDUtLjc4LTEuMDctMS40NS0xLjgyLTEuOTZMMTcgNC40MSAxNS41OSAzbC0yLjE3IDIuMTdDMTIuOTYgNS4wNiAxMi40OSA1IDEyIDVjLS40OSAwLS45Ni4wNi0xLjQxLjE3TDguNDEgMyA3IDQuNDFsMS42MiAxLjYzQzcuODggNi41NSA3LjI2IDcuMjIgNi44MSA4SDR2MmgyLjA5Yy0uMDUuMzMtLjA5LjY2LS4wOSAxdjFINHYyaDJ2MWMwIC4zNC4wNC42Ny4wOSAxSDR2MmgyLjgxYzEuMDQgMS43OSAyLjk3IDMgNS4xOSAzczQuMTUtMS4yMSA1LjE5LTNIMjB2LTJoLTIuMDljLjA1LS4zMy4wOS0uNjYuMDktMXYtMWgydi0yaC0ydi0xYzAtLjM0LS4wNC0uNjctLjA5LTFIMjBWOHptLTYgOGgtNHYtMmg0djJ6bTAtNGgtNHYtMmg0djJ6Ii8+CiAgPC9nPgo8L3N2Zz4K);
    --jp-icon-build: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIHZpZXdCb3g9IjAgMCAyNCAyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE0LjkgMTcuNDVDMTYuMjUgMTcuNDUgMTcuMzUgMTYuMzUgMTcuMzUgMTVDMTcuMzUgMTMuNjUgMTYuMjUgMTIuNTUgMTQuOSAxMi41NUMxMy41NCAxMi41NSAxMi40NSAxMy42NSAxMi40NSAxNUMxMi40NSAxNi4zNSAxMy41NCAxNy40NSAxNC45IDE3LjQ1Wk0yMC4xIDE1LjY4TDIxLjU4IDE2Ljg0QzIxLjcxIDE2Ljk1IDIxLjc1IDE3LjEzIDIxLjY2IDE3LjI5TDIwLjI2IDE5LjcxQzIwLjE3IDE5Ljg2IDIwIDE5LjkyIDE5LjgzIDE5Ljg2TDE4LjA5IDE5LjE2QzE3LjczIDE5LjQ0IDE3LjMzIDE5LjY3IDE2LjkxIDE5Ljg1TDE2LjY0IDIxLjdDMTYuNjIgMjEuODcgMTYuNDcgMjIgMTYuMyAyMkgxMy41QzEzLjMyIDIyIDEzLjE4IDIxLjg3IDEzLjE1IDIxLjdMMTIuODkgMTkuODVDMTIuNDYgMTkuNjcgMTIuMDcgMTkuNDQgMTEuNzEgMTkuMTZMOS45NjAwMiAxOS44NkM5LjgxMDAyIDE5LjkyIDkuNjIwMDIgMTkuODYgOS41NDAwMiAxOS43MUw4LjE0MDAyIDE3LjI5QzguMDUwMDIgMTcuMTMgOC4wOTAwMiAxNi45NSA4LjIyMDAyIDE2Ljg0TDkuNzAwMDIgMTUuNjhMOS42NTAwMSAxNUw5LjcwMDAyIDE0LjMxTDguMjIwMDIgMTMuMTZDOC4wOTAwMiAxMy4wNSA4LjA1MDAyIDEyLjg2IDguMTQwMDIgMTIuNzFMOS41NDAwMiAxMC4yOUM5LjYyMDAyIDEwLjEzIDkuODEwMDIgMTAuMDcgOS45NjAwMiAxMC4xM0wxMS43MSAxMC44NEMxMi4wNyAxMC41NiAxMi40NiAxMC4zMiAxMi44OSAxMC4xNUwxMy4xNSA4LjI4OTk4QzEzLjE4IDguMTI5OTggMTMuMzIgNy45OTk5OCAxMy41IDcuOTk5OThIMTYuM0MxNi40NyA3Ljk5OTk4IDE2LjYyIDguMTI5OTggMTYuNjQgOC4yODk5OEwxNi45MSAxMC4xNUMxNy4zMyAxMC4zMiAxNy43MyAxMC41NiAxOC4wOSAxMC44NEwxOS44MyAxMC4xM0MyMCAxMC4wNyAyMC4xNyAxMC4xMyAyMC4yNiAxMC4yOUwyMS42NiAxMi43MUMyMS43NSAxMi44NiAyMS43MSAxMy4wNSAyMS41OCAxMy4xNkwyMC4xIDE0LjMxTDIwLjE1IDE1TDIwLjEgMTUuNjhaIi8+CiAgICA8cGF0aCBkPSJNNy4zMjk2NiA3LjQ0NDU0QzguMDgzMSA3LjAwOTU0IDguMzM5MzIgNi4wNTMzMiA3LjkwNDMyIDUuMjk5ODhDNy40NjkzMiA0LjU0NjQzIDYuNTA4MSA0LjI4MTU2IDUuNzU0NjYgNC43MTY1NkM1LjM5MTc2IDQuOTI2MDggNS4xMjY5NSA1LjI3MTE4IDUuMDE4NDkgNS42NzU5NEM0LjkxMDA0IDYuMDgwNzEgNC45NjY4MiA2LjUxMTk4IDUuMTc2MzQgNi44NzQ4OEM1LjYxMTM0IDcuNjI4MzIgNi41NzYyMiA3Ljg3OTU0IDcuMzI5NjYgNy40NDQ1NFpNOS42NTcxOCA0Ljc5NTkzTDEwLjg2NzIgNC45NTE3OUMxMC45NjI4IDQuOTc3NDEgMTEuMDQwMiA1LjA3MTMzIDExLjAzODIgNS4xODc5M0wxMS4wMzg4IDYuOTg4OTNDMTEuMDQ1NSA3LjEwMDU0IDEwLjk2MTYgNy4xOTUxOCAxMC44NTUgNy4yMTA1NEw5LjY2MDAxIDcuMzgwODNMOS4yMzkxNSA4LjEzMTg4TDkuNjY5NjEgOS4yNTc0NUM5LjcwNzI5IDkuMzYyNzEgOS42NjkzNCA5LjQ3Njk5IDkuNTc0MDggOS41MzE5OUw4LjAxNTIzIDEwLjQzMkM3LjkxMTMxIDEwLjQ5MiA3Ljc5MzM3IDEwLjQ2NzcgNy43MjEwNSAxMC4zODI0TDYuOTg3NDggOS40MzE4OEw2LjEwOTMxIDkuNDMwODNMNS4zNDcwNCAxMC4zOTA1QzUuMjg5MDkgMTAuNDcwMiA1LjE3MzgzIDEwLjQ5MDUgNS4wNzE4NyAxMC40MzM5TDMuNTEyNDUgOS41MzI5M0MzLjQxMDQ5IDkuNDc2MzMgMy4zNzY0NyA5LjM1NzQxIDMuNDEwNzUgOS4yNTY3OUwzLjg2MzQ3IDguMTQwOTNMMy42MTc0OSA3Ljc3NDg4TDMuNDIzNDcgNy4zNzg4M0wyLjIzMDc1IDcuMjEyOTdDMi4xMjY0NyA3LjE5MjM1IDIuMDQwNDkgNy4xMDM0MiAyLjA0MjQ1IDYuOTg2ODJMMi4wNDE4NyA1LjE4NTgyQzIuMDQzODMgNS4wNjkyMiAyLjExOTA5IDQuOTc5NTggMi4yMTcwNCA0Ljk2OTIyTDMuNDIwNjUgNC43OTM5M0wzLjg2NzQ5IDQuMDI3ODhMMy40MTEwNSAyLjkxNzMxQzMuMzczMzcgMi44MTIwNCAzLjQxMTMxIDIuNjk3NzYgMy41MTUyMyAyLjYzNzc2TDUuMDc0MDggMS43Mzc3NkM1LjE2OTM0IDEuNjgyNzYgNS4yODcyOSAxLjcwNzA0IDUuMzU5NjEgMS43OTIzMUw2LjExOTE1IDIuNzI3ODhMNi45ODAwMSAyLjczODkzTDcuNzI0OTYgMS43ODkyMkM3Ljc5MTU2IDEuNzA0NTggNy45MTU0OCAxLjY3OTIyIDguMDA4NzkgMS43NDA4Mkw5LjU2ODIxIDIuNjQxODJDOS42NzAxNyAyLjY5ODQyIDkuNzEyODUgMi44MTIzNCA5LjY4NzIzIDIuOTA3OTdMOS4yMTcxOCA0LjAzMzgzTDkuNDYzMTYgNC4zOTk4OEw5LjY1NzE4IDQuNzk1OTNaIi8+CiAgPC9nPgo8L3N2Zz4K);
    --jp-icon-caret-down-empty-thin: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwb2x5Z29uIGNsYXNzPSJzdDEiIHBvaW50cz0iOS45LDEzLjYgMy42LDcuNCA0LjQsNi42IDkuOSwxMi4yIDE1LjQsNi43IDE2LjEsNy40ICIvPgoJPC9nPgo8L3N2Zz4K);
    --jp-icon-caret-down-empty: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiIHNoYXBlLXJlbmRlcmluZz0iZ2VvbWV0cmljUHJlY2lzaW9uIj4KICAgIDxwYXRoIGQ9Ik01LjIsNS45TDksOS43bDMuOC0zLjhsMS4yLDEuMmwtNC45LDVsLTQuOS01TDUuMiw1Ljl6Ii8+CiAgPC9nPgo8L3N2Zz4K);
    --jp-icon-caret-down: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiIHNoYXBlLXJlbmRlcmluZz0iZ2VvbWV0cmljUHJlY2lzaW9uIj4KICAgIDxwYXRoIGQ9Ik01LjIsNy41TDksMTEuMmwzLjgtMy44SDUuMnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-caret-left: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwYXRoIGQ9Ik0xMC44LDEyLjhMNy4xLDlsMy44LTMuOGwwLDcuNkgxMC44eiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-caret-right: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiIHNoYXBlLXJlbmRlcmluZz0iZ2VvbWV0cmljUHJlY2lzaW9uIj4KICAgIDxwYXRoIGQ9Ik03LjIsNS4yTDEwLjksOWwtMy44LDMuOFY1LjJINy4yeiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-caret-up-empty-thin: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwb2x5Z29uIGNsYXNzPSJzdDEiIHBvaW50cz0iMTUuNCwxMy4zIDkuOSw3LjcgNC40LDEzLjIgMy42LDEyLjUgOS45LDYuMyAxNi4xLDEyLjYgIi8+Cgk8L2c+Cjwvc3ZnPgo=);
    --jp-icon-caret-up: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSIgc2hhcGUtcmVuZGVyaW5nPSJnZW9tZXRyaWNQcmVjaXNpb24iPgoJCTxwYXRoIGQ9Ik01LjIsMTAuNUw5LDYuOGwzLjgsMy44SDUuMnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-case-sensitive: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KICA8ZyBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiM0MTQxNDEiPgogICAgPHJlY3QgeD0iMiIgeT0iMiIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2Ii8+CiAgPC9nPgogIDxnIGNsYXNzPSJqcC1pY29uLWFjY2VudDIiIGZpbGw9IiNGRkYiPgogICAgPHBhdGggZD0iTTcuNiw4aDAuOWwzLjUsOGgtMS4xTDEwLDE0SDZsLTAuOSwySDRMNy42LDh6IE04LDkuMUw2LjQsMTNoMy4yTDgsOS4xeiIvPgogICAgPHBhdGggZD0iTTE2LjYsOS44Yy0wLjIsMC4xLTAuNCwwLjEtMC43LDAuMWMtMC4yLDAtMC40LTAuMS0wLjYtMC4yYy0wLjEtMC4xLTAuMi0wLjQtMC4yLTAuNyBjLTAuMywwLjMtMC42LDAuNS0wLjksMC43Yy0wLjMsMC4xLTAuNywwLjItMS4xLDAuMmMtMC4zLDAtMC41LDAtMC43LTAuMWMtMC4yLTAuMS0wLjQtMC4yLTAuNi0wLjNjLTAuMi0wLjEtMC4zLTAuMy0wLjQtMC41IGMtMC4xLTAuMi0wLjEtMC40LTAuMS0wLjdjMC0wLjMsMC4xLTAuNiwwLjItMC44YzAuMS0wLjIsMC4zLTAuNCwwLjQtMC41QzEyLDcsMTIuMiw2LjksMTIuNSw2LjhjMC4yLTAuMSwwLjUtMC4xLDAuNy0wLjIgYzAuMy0wLjEsMC41LTAuMSwwLjctMC4xYzAuMiwwLDAuNC0wLjEsMC42LTAuMWMwLjIsMCwwLjMtMC4xLDAuNC0wLjJjMC4xLTAuMSwwLjItMC4yLDAuMi0wLjRjMC0xLTEuMS0xLTEuMy0xIGMtMC40LDAtMS40LDAtMS40LDEuMmgtMC45YzAtMC40LDAuMS0wLjcsMC4yLTFjMC4xLTAuMiwwLjMtMC40LDAuNS0wLjZjMC4yLTAuMiwwLjUtMC4zLDAuOC0wLjNDMTMuMyw0LDEzLjYsNCwxMy45LDQgYzAuMywwLDAuNSwwLDAuOCwwLjFjMC4zLDAsMC41LDAuMSwwLjcsMC4yYzAuMiwwLjEsMC40LDAuMywwLjUsMC41QzE2LDUsMTYsNS4yLDE2LDUuNnYyLjljMCwwLjIsMCwwLjQsMCwwLjUgYzAsMC4xLDAuMSwwLjIsMC4zLDAuMmMwLjEsMCwwLjIsMCwwLjMsMFY5Ljh6IE0xNS4yLDYuOWMtMS4yLDAuNi0zLjEsMC4yLTMuMSwxLjRjMCwxLjQsMy4xLDEsMy4xLTAuNVY2Ljl6Ii8+CiAgPC9nPgo8L3N2Zz4K);
    --jp-icon-check: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxwYXRoIGQ9Ik05IDE2LjE3TDQuODMgMTJsLTEuNDIgMS40MUw5IDE5IDIxIDdsLTEuNDEtMS40MXoiLz4KICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-circle-empty: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyIDJDNi40NyAyIDIgNi40NyAyIDEyczQuNDcgMTAgMTAgMTAgMTAtNC40NyAxMC0xMFMxNy41MyAyIDEyIDJ6bTAgMThjLTQuNDEgMC04LTMuNTktOC04czMuNTktOCA4LTggOCAzLjU5IDggOC0zLjU5IDgtOCA4eiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-circle: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMTggMTgiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPGNpcmNsZSBjeD0iOSIgY3k9IjkiIHI9IjgiLz4KICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-clear: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8bWFzayBpZD0iZG9udXRIb2xlIj4KICAgIDxyZWN0IHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgZmlsbD0id2hpdGUiIC8+CiAgICA8Y2lyY2xlIGN4PSIxMiIgY3k9IjEyIiByPSI4IiBmaWxsPSJibGFjayIvPgogIDwvbWFzaz4KCiAgPGcgY2xhc3M9ImpwLWljb24zIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxyZWN0IGhlaWdodD0iMTgiIHdpZHRoPSIyIiB4PSIxMSIgeT0iMyIgdHJhbnNmb3JtPSJyb3RhdGUoMzE1LCAxMiwgMTIpIi8+CiAgICA8Y2lyY2xlIGN4PSIxMiIgY3k9IjEyIiByPSIxMCIgbWFzaz0idXJsKCNkb251dEhvbGUpIi8+CiAgPC9nPgo8L3N2Zz4K);
    --jp-icon-close: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbi1ub25lIGpwLWljb24tc2VsZWN0YWJsZS1pbnZlcnNlIGpwLWljb24zLWhvdmVyIiBmaWxsPSJub25lIj4KICAgIDxjaXJjbGUgY3g9IjEyIiBjeT0iMTIiIHI9IjExIi8+CiAgPC9nPgoKICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIGpwLWljb24tYWNjZW50Mi1ob3ZlciIgZmlsbD0iIzYxNjE2MSI+CiAgICA8cGF0aCBkPSJNMTkgNi40MUwxNy41OSA1IDEyIDEwLjU5IDYuNDEgNSA1IDYuNDEgMTAuNTkgMTIgNSAxNy41OSA2LjQxIDE5IDEyIDEzLjQxIDE3LjU5IDE5IDE5IDE3LjU5IDEzLjQxIDEyeiIvPgogIDwvZz4KCiAgPGcgY2xhc3M9ImpwLWljb24tbm9uZSBqcC1pY29uLWJ1c3kiIGZpbGw9Im5vbmUiPgogICAgPGNpcmNsZSBjeD0iMTIiIGN5PSIxMiIgcj0iNyIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-code-check: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNCIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBzaGFwZS1yZW5kZXJpbmc9Imdlb21ldHJpY1ByZWNpc2lvbiI+CiAgICA8cGF0aCBkPSJNNi41OSwzLjQxTDIsOEw2LjU5LDEyLjZMOCwxMS4xOEw0LjgyLDhMOCw0LjgyTDYuNTksMy40MU0xMi40MSwzLjQxTDExLDQuODJMMTQuMTgsOEwxMSwxMS4xOEwxMi40MSwxMi42TDE3LDhMMTIuNDEsMy40MU0yMS41OSwxMS41OUwxMy41LDE5LjY4TDkuODMsMTZMOC40MiwxNy40MUwxMy41LDIyLjVMMjMsMTNMMjEuNTksMTEuNTlaIiAvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-code: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjIiIGhlaWdodD0iMjIiIHZpZXdCb3g9IjAgMCAyOCAyOCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CgkJPHBhdGggZD0iTTExLjQgMTguNkw2LjggMTRMMTEuNCA5LjRMMTAgOEw0IDE0TDEwIDIwTDExLjQgMTguNlpNMTYuNiAxOC42TDIxLjIgMTRMMTYuNiA5LjRMMTggOEwyNCAxNEwxOCAyMEwxNi42IDE4LjZWMTguNloiLz4KCTwvZz4KPC9zdmc+Cg==);
    --jp-icon-collapse-all: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGgKICAgICAgICAgICAgZD0iTTggMmMxIDAgMTEgMCAxMiAwczIgMSAyIDJjMCAxIDAgMTEgMCAxMnMwIDItMiAyQzIwIDE0IDIwIDQgMjAgNFMxMCA0IDYgNGMwLTIgMS0yIDItMnoiIC8+CiAgICAgICAgPHBhdGgKICAgICAgICAgICAgZD0iTTE4IDhjMC0xLTEtMi0yLTJTNSA2IDQgNnMtMiAxLTIgMmMwIDEgMCAxMSAwIDEyczEgMiAyIDJjMSAwIDExIDAgMTIgMHMyLTEgMi0yYzAtMSAwLTExIDAtMTJ6bS0yIDB2MTJINFY4eiIgLz4KICAgICAgICA8cGF0aCBkPSJNNiAxM3YyaDh2LTJ6IiAvPgogICAgPC9nPgo8L3N2Zz4K);
    --jp-icon-console: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwMCAyMDAiPgogIDxnIGNsYXNzPSJqcC1jb25zb2xlLWljb24tYmFja2dyb3VuZC1jb2xvciBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiMwMjg4RDEiPgogICAgPHBhdGggZD0iTTIwIDE5LjhoMTYwdjE1OS45SDIweiIvPgogIDwvZz4KICA8ZyBjbGFzcz0ianAtY29uc29sZS1pY29uLWNvbG9yIGpwLWljb24tc2VsZWN0YWJsZS1pbnZlcnNlIiBmaWxsPSIjZmZmIj4KICAgIDxwYXRoIGQ9Ik0xMDUgMTI3LjNoNDB2MTIuOGgtNDB6TTUxLjEgNzdMNzQgOTkuOWwtMjMuMyAyMy4zIDEwLjUgMTAuNSAyMy4zLTIzLjNMOTUgOTkuOSA4NC41IDg5LjQgNjEuNiA2Ni41eiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-copy: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMTggMTgiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTExLjksMUgzLjJDMi40LDEsMS43LDEuNywxLjcsMi41djEwLjJoMS41VjIuNWg4LjdWMXogTTE0LjEsMy45aC04Yy0wLjgsMC0xLjUsMC43LTEuNSwxLjV2MTAuMmMwLDAuOCwwLjcsMS41LDEuNSwxLjVoOCBjMC44LDAsMS41LTAuNywxLjUtMS41VjUuNEMxNS41LDQuNiwxNC45LDMuOSwxNC4xLDMuOXogTTE0LjEsMTUuNWgtOFY1LjRoOFYxNS41eiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-copyright: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIGVuYWJsZS1iYWNrZ3JvdW5kPSJuZXcgMCAwIDI0IDI0IiBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCI+CiAgPGcgY2xhc3M9ImpwLWljb24zIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxwYXRoIGQ9Ik0xMS44OCw5LjE0YzEuMjgsMC4wNiwxLjYxLDEuMTUsMS42MywxLjY2aDEuNzljLTAuMDgtMS45OC0xLjQ5LTMuMTktMy40NS0zLjE5QzkuNjQsNy42MSw4LDksOCwxMi4xNCBjMCwxLjk0LDAuOTMsNC4yNCwzLjg0LDQuMjRjMi4yMiwwLDMuNDEtMS42NSwzLjQ0LTIuOTVoLTEuNzljLTAuMDMsMC41OS0wLjQ1LDEuMzgtMS42MywxLjQ0QzEwLjU1LDE0LjgzLDEwLDEzLjgxLDEwLDEyLjE0IEMxMCw5LjI1LDExLjI4LDkuMTYsMTEuODgsOS4xNHogTTEyLDJDNi40OCwyLDIsNi40OCwyLDEyczQuNDgsMTAsMTAsMTBzMTAtNC40OCwxMC0xMFMxNy41MiwyLDEyLDJ6IE0xMiwyMGMtNC40MSwwLTgtMy41OS04LTggczMuNTktOCw4LThzOCwzLjU5LDgsOFMxNi40MSwyMCwxMiwyMHoiLz4KICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-cut: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTkuNjQgNy42NGMuMjMtLjUuMzYtMS4wNS4zNi0xLjY0IDAtMi4yMS0xLjc5LTQtNC00UzIgMy43OSAyIDZzMS43OSA0IDQgNGMuNTkgMCAxLjE0LS4xMyAxLjY0LS4zNkwxMCAxMmwtMi4zNiAyLjM2QzcuMTQgMTQuMTMgNi41OSAxNCA2IDE0Yy0yLjIxIDAtNCAxLjc5LTQgNHMxLjc5IDQgNCA0IDQtMS43OSA0LTRjMC0uNTktLjEzLTEuMTQtLjM2LTEuNjRMMTIgMTRsNyA3aDN2LTFMOS42NCA3LjY0ek02IDhjLTEuMSAwLTItLjg5LTItMnMuOS0yIDItMiAyIC44OSAyIDItLjkgMi0yIDJ6bTAgMTJjLTEuMSAwLTItLjg5LTItMnMuOS0yIDItMiAyIC44OSAyIDItLjkgMi0yIDJ6bTYtNy41Yy0uMjggMC0uNS0uMjItLjUtLjVzLjIyLS41LjUtLjUuNS4yMi41LjUtLjIyLjUtLjUuNXpNMTkgM2wtNiA2IDIgMiA3LTdWM3oiLz4KICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-delete: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCIgd2lkdGg9IjE2cHgiIGhlaWdodD0iMTZweCI+CiAgICA8cGF0aCBkPSJNMCAwaDI0djI0SDB6IiBmaWxsPSJub25lIiAvPgogICAgPHBhdGggY2xhc3M9ImpwLWljb24zIiBmaWxsPSIjNjI2MjYyIiBkPSJNNiAxOWMwIDEuMS45IDIgMiAyaDhjMS4xIDAgMi0uOSAyLTJWN0g2djEyek0xOSA0aC0zLjVsLTEtMWgtNWwtMSAxSDV2MmgxNFY0eiIgLz4KPC9zdmc+Cg==);
    --jp-icon-download: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE5IDloLTRWM0g5djZINWw3IDcgNy03ek01IDE4djJoMTR2LTJINXoiLz4KICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-duplicate: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTQiIGhlaWdodD0iMTQiIHZpZXdCb3g9IjAgMCAxNCAxNCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KPHBhdGggY2xhc3M9ImpwLWljb24zIiBmaWxsLXJ1bGU9ImV2ZW5vZGQiIGNsaXAtcnVsZT0iZXZlbm9kZCIgZD0iTTIuNzk5OTggMC44NzVIOC44OTU4MkM5LjIwMDYxIDAuODc1IDkuNDQ5OTggMS4xMzkxNCA5LjQ0OTk4IDEuNDYxOThDOS40NDk5OCAxLjc4NDgyIDkuMjAwNjEgMi4wNDg5NiA4Ljg5NTgyIDIuMDQ4OTZIMy4zNTQxNUMzLjA0OTM2IDIuMDQ4OTYgMi43OTk5OCAyLjMxMzEgMi43OTk5OCAyLjYzNTk0VjkuNjc5NjlDMi43OTk5OCAxMC4wMDI1IDIuNTUwNjEgMTAuMjY2NyAyLjI0NTgyIDEwLjI2NjdDMS45NDEwMyAxMC4yNjY3IDEuNjkxNjUgMTAuMDAyNSAxLjY5MTY1IDkuNjc5NjlWMi4wNDg5NkMxLjY5MTY1IDEuNDAzMjggMi4xOTA0IDAuODc1IDIuNzk5OTggMC44NzVaTTUuMzY2NjUgMTEuOVY0LjU1SDExLjA4MzNWMTEuOUg1LjM2NjY1Wk00LjE0MTY1IDQuMTQxNjdDNC4xNDE2NSAzLjY5MDYzIDQuNTA3MjggMy4zMjUgNC45NTgzMiAzLjMyNUgxMS40OTE3QzExLjk0MjcgMy4zMjUgMTIuMzA4MyAzLjY5MDYzIDEyLjMwODMgNC4xNDE2N1YxMi4zMDgzQzEyLjMwODMgMTIuNzU5NCAxMS45NDI3IDEzLjEyNSAxMS40OTE3IDEzLjEyNUg0Ljk1ODMyQzQuNTA3MjggMTMuMTI1IDQuMTQxNjUgMTIuNzU5NCA0LjE0MTY1IDEyLjMwODNWNC4xNDE2N1oiIGZpbGw9IiM2MTYxNjEiLz4KPHBhdGggY2xhc3M9ImpwLWljb24zIiBkPSJNOS40MzU3NCA4LjI2NTA3SDguMzY0MzFWOS4zMzY1QzguMzY0MzEgOS40NTQzNSA4LjI2Nzg4IDkuNTUwNzggOC4xNTAwMiA5LjU1MDc4QzguMDMyMTcgOS41NTA3OCA3LjkzNTc0IDkuNDU0MzUgNy45MzU3NCA5LjMzNjVWOC4yNjUwN0g2Ljg2NDMxQzYuNzQ2NDUgOC4yNjUwNyA2LjY1MDAyIDguMTY4NjQgNi42NTAwMiA4LjA1MDc4QzYuNjUwMDIgNy45MzI5MiA2Ljc0NjQ1IDcuODM2NSA2Ljg2NDMxIDcuODM2NUg3LjkzNTc0VjYuNzY1MDdDNy45MzU3NCA2LjY0NzIxIDguMDMyMTcgNi41NTA3OCA4LjE1MDAyIDYuNTUwNzhDOC4yNjc4OCA2LjU1MDc4IDguMzY0MzEgNi42NDcyMSA4LjM2NDMxIDYuNzY1MDdWNy44MzY1SDkuNDM1NzRDOS41NTM2IDcuODM2NSA5LjY1MDAyIDcuOTMyOTIgOS42NTAwMiA4LjA1MDc4QzkuNjUwMDIgOC4xNjg2NCA5LjU1MzYgOC4yNjUwNyA5LjQzNTc0IDguMjY1MDdaIiBmaWxsPSIjNjE2MTYxIiBzdHJva2U9IiM2MTYxNjEiIHN0cm9rZS13aWR0aD0iMC41Ii8+Cjwvc3ZnPgo=);
    --jp-icon-edit: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTMgMTcuMjVWMjFoMy43NUwxNy44MSA5Ljk0bC0zLjc1LTMuNzVMMyAxNy4yNXpNMjAuNzEgNy4wNGMuMzktLjM5LjM5LTEuMDIgMC0xLjQxbC0yLjM0LTIuMzRjLS4zOS0uMzktMS4wMi0uMzktMS40MSAwbC0xLjgzIDEuODMgMy43NSAzLjc1IDEuODMtMS44M3oiLz4KICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-ellipses: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPGNpcmNsZSBjeD0iNSIgY3k9IjEyIiByPSIyIi8+CiAgICA8Y2lyY2xlIGN4PSIxMiIgY3k9IjEyIiByPSIyIi8+CiAgICA8Y2lyY2xlIGN4PSIxOSIgY3k9IjEyIiByPSIyIi8+CiAgPC9nPgo8L3N2Zz4K);
    --jp-icon-error: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KPGcgY2xhc3M9ImpwLWljb24zIiBmaWxsPSIjNjE2MTYxIj48Y2lyY2xlIGN4PSIxMiIgY3k9IjE5IiByPSIyIi8+PHBhdGggZD0iTTEwIDNoNHYxMmgtNHoiLz48L2c+CjxwYXRoIGZpbGw9Im5vbmUiIGQ9Ik0wIDBoMjR2MjRIMHoiLz4KPC9zdmc+Cg==);
    --jp-icon-expand-all: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGgKICAgICAgICAgICAgZD0iTTggMmMxIDAgMTEgMCAxMiAwczIgMSAyIDJjMCAxIDAgMTEgMCAxMnMwIDItMiAyQzIwIDE0IDIwIDQgMjAgNFMxMCA0IDYgNGMwLTIgMS0yIDItMnoiIC8+CiAgICAgICAgPHBhdGgKICAgICAgICAgICAgZD0iTTE4IDhjMC0xLTEtMi0yLTJTNSA2IDQgNnMtMiAxLTIgMmMwIDEgMCAxMSAwIDEyczEgMiAyIDJjMSAwIDExIDAgMTIgMHMyLTEgMi0yYzAtMSAwLTExIDAtMTJ6bS0yIDB2MTJINFY4eiIgLz4KICAgICAgICA8cGF0aCBkPSJNMTEgMTBIOXYzSDZ2MmgzdjNoMnYtM2gzdi0yaC0zeiIgLz4KICAgIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-extension: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTIwLjUgMTFIMTlWN2MwLTEuMS0uOS0yLTItMmgtNFYzLjVDMTMgMi4xMiAxMS44OCAxIDEwLjUgMVM4IDIuMTIgOCAzLjVWNUg0Yy0xLjEgMC0xLjk5LjktMS45OSAydjMuOEgzLjVjMS40OSAwIDIuNyAxLjIxIDIuNyAyLjdzLTEuMjEgMi43LTIuNyAyLjdIMlYyMGMwIDEuMS45IDIgMiAyaDMuOHYtMS41YzAtMS40OSAxLjIxLTIuNyAyLjctMi43IDEuNDkgMCAyLjcgMS4yMSAyLjcgMi43VjIySDE3YzEuMSAwIDItLjkgMi0ydi00aDEuNWMxLjM4IDAgMi41LTEuMTIgMi41LTIuNVMyMS44OCAxMSAyMC41IDExeiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-fast-forward: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTQgMThsOC41LTZMNCA2djEyem05LTEydjEybDguNS02TDEzIDZ6Ii8+CiAgICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-file-upload: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTkgMTZoNnYtNmg0bC03LTctNyA3aDR6bS00IDJoMTR2Mkg1eiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-file: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTkuMyA4LjJsLTUuNS01LjVjLS4zLS4zLS43LS41LTEuMi0uNUgzLjljLS44LjEtMS42LjktMS42IDEuOHYxNC4xYzAgLjkuNyAxLjYgMS42IDEuNmgxNC4yYy45IDAgMS42LS43IDEuNi0xLjZWOS40Yy4xLS41LS4xLS45LS40LTEuMnptLTUuOC0zLjNsMy40IDMuNmgtMy40VjQuOXptMy45IDEyLjdINC43Yy0uMSAwLS4yIDAtLjItLjJWNC43YzAtLjIuMS0uMy4yLS4zaDcuMnY0LjRzMCAuOC4zIDEuMWMuMy4zIDEuMS4zIDEuMS4zaDQuM3Y3LjJzLS4xLjItLjIuMnoiLz4KPC9zdmc+Cg==);
    --jp-icon-filter-dot: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiNGRkYiPgogICAgPHBhdGggZD0iTTE0LDEyVjE5Ljg4QzE0LjA0LDIwLjE4IDEzLjk0LDIwLjUgMTMuNzEsMjAuNzFDMTMuMzIsMjEuMSAxMi42OSwyMS4xIDEyLjMsMjAuNzFMMTAuMjksMTguN0MxMC4wNiwxOC40NyA5Ljk2LDE4LjE2IDEwLDE3Ljg3VjEySDkuOTdMNC4yMSw0LjYyQzMuODcsNC4xOSAzLjk1LDMuNTYgNC4zOCwzLjIyQzQuNTcsMy4wOCA0Ljc4LDMgNSwzVjNIMTlWM0MxOS4yMiwzIDE5LjQzLDMuMDggMTkuNjIsMy4yMkMyMC4wNSwzLjU2IDIwLjEzLDQuMTkgMTkuNzksNC42MkwxNC4wMywxMkgxNFoiIC8+CiAgPC9nPgogIDxnIGNsYXNzPSJqcC1pY29uLWRvdCIgZmlsbD0iI0ZGRiI+CiAgICA8Y2lyY2xlIGN4PSIxOCIgY3k9IjE3IiByPSIzIj48L2NpcmNsZT4KICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-filter-list: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEwIDE4aDR2LTJoLTR2MnpNMyA2djJoMThWNkgzem0zIDdoMTJ2LTJINnYyeiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-filter: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiNGRkYiPgogICAgPHBhdGggZD0iTTE0LDEyVjE5Ljg4QzE0LjA0LDIwLjE4IDEzLjk0LDIwLjUgMTMuNzEsMjAuNzFDMTMuMzIsMjEuMSAxMi42OSwyMS4xIDEyLjMsMjAuNzFMMTAuMjksMTguN0MxMC4wNiwxOC40NyA5Ljk2LDE4LjE2IDEwLDE3Ljg3VjEySDkuOTdMNC4yMSw0LjYyQzMuODcsNC4xOSAzLjk1LDMuNTYgNC4zOCwzLjIyQzQuNTcsMy4wOCA0Ljc4LDMgNSwzVjNIMTlWM0MxOS4yMiwzIDE5LjQzLDMuMDggMTkuNjIsMy4yMkMyMC4wNSwzLjU2IDIwLjEzLDQuMTkgMTkuNzksNC42MkwxNC4wMywxMkgxNFoiIC8+CiAgPC9nPgo8L3N2Zz4K);
    --jp-icon-folder-favorite: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIGhlaWdodD0iMjRweCIgdmlld0JveD0iMCAwIDI0IDI0IiB3aWR0aD0iMjRweCIgZmlsbD0iIzAwMDAwMCI+CiAgPHBhdGggZD0iTTAgMGgyNHYyNEgwVjB6IiBmaWxsPSJub25lIi8+PHBhdGggY2xhc3M9ImpwLWljb24zIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iIzYxNjE2MSIgZD0iTTIwIDZoLThsLTItMkg0Yy0xLjEgMC0yIC45LTIgMnYxMmMwIDEuMS45IDIgMiAyaDE2YzEuMSAwIDItLjkgMi0yVjhjMC0xLjEtLjktMi0yLTJ6bS0yLjA2IDExTDE1IDE1LjI4IDEyLjA2IDE3bC43OC0zLjMzLTIuNTktMi4yNCAzLjQxLS4yOUwxNSA4bDEuMzQgMy4xNCAzLjQxLjI5LTIuNTkgMi4yNC43OCAzLjMzeiIvPgo8L3N2Zz4K);
    --jp-icon-folder: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTAgNEg0Yy0xLjEgMC0xLjk5LjktMS45OSAyTDIgMThjMCAxLjEuOSAyIDIgMmgxNmMxLjEgMCAyLS45IDItMlY4YzAtMS4xLS45LTItMi0yaC04bC0yLTJ6Ii8+Cjwvc3ZnPgo=);
    --jp-icon-home: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIGhlaWdodD0iMjRweCIgdmlld0JveD0iMCAwIDI0IDI0IiB3aWR0aD0iMjRweCIgZmlsbD0iIzAwMDAwMCI+CiAgPHBhdGggZD0iTTAgMGgyNHYyNEgweiIgZmlsbD0ibm9uZSIvPjxwYXRoIGNsYXNzPSJqcC1pY29uMyBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiM2MTYxNjEiIGQ9Ik0xMCAyMHYtNmg0djZoNXYtOGgzTDEyIDMgMiAxMmgzdjh6Ii8+Cjwvc3ZnPgo=);
    --jp-icon-html5: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDUxMiA1MTIiPgogIDxwYXRoIGNsYXNzPSJqcC1pY29uMCBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiMwMDAiIGQ9Ik0xMDguNCAwaDIzdjIyLjhoMjEuMlYwaDIzdjY5aC0yM1Y0NmgtMjF2MjNoLTIzLjJNMjA2IDIzaC0yMC4zVjBoNjMuN3YyM0gyMjl2NDZoLTIzbTUzLjUtNjloMjQuMWwxNC44IDI0LjNMMzEzLjIgMGgyNC4xdjY5aC0yM1YzNC44bC0xNi4xIDI0LjgtMTYuMS0yNC44VjY5aC0yMi42bTg5LjItNjloMjN2NDYuMmgzMi42VjY5aC01NS42Ii8+CiAgPHBhdGggY2xhc3M9ImpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iI2U0NGQyNiIgZD0iTTEwNy42IDQ3MWwtMzMtMzcwLjRoMzYyLjhsLTMzIDM3MC4yTDI1NS43IDUxMiIvPgogIDxwYXRoIGNsYXNzPSJqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiNmMTY1MjkiIGQ9Ik0yNTYgNDgwLjVWMTMxaDE0OC4zTDM3NiA0NDciLz4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1zZWxlY3RhYmxlLWludmVyc2UiIGZpbGw9IiNlYmViZWIiIGQ9Ik0xNDIgMTc2LjNoMTE0djQ1LjRoLTY0LjJsNC4yIDQ2LjVoNjB2NDUuM0gxNTQuNG0yIDIyLjhIMjAybDMuMiAzNi4zIDUwLjggMTMuNnY0Ny40bC05My4yLTI2Ii8+CiAgPHBhdGggY2xhc3M9ImpwLWljb24tc2VsZWN0YWJsZS1pbnZlcnNlIiBmaWxsPSIjZmZmIiBkPSJNMzY5LjYgMTc2LjNIMjU1Ljh2NDUuNGgxMDkuNm0tNC4xIDQ2LjVIMjU1Ljh2NDUuNGg1NmwtNS4zIDU5LTUwLjcgMTMuNnY0Ny4ybDkzLTI1LjgiLz4KPC9zdmc+Cg==);
    --jp-icon-image: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1icmFuZDQganAtaWNvbi1zZWxlY3RhYmxlLWludmVyc2UiIGZpbGw9IiNGRkYiIGQ9Ik0yLjIgMi4yaDE3LjV2MTcuNUgyLjJ6Ii8+CiAgPHBhdGggY2xhc3M9ImpwLWljb24tYnJhbmQwIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iIzNGNTFCNSIgZD0iTTIuMiAyLjJ2MTcuNWgxNy41bC4xLTE3LjVIMi4yem0xMi4xIDIuMmMxLjIgMCAyLjIgMSAyLjIgMi4ycy0xIDIuMi0yLjIgMi4yLTIuMi0xLTIuMi0yLjIgMS0yLjIgMi4yLTIuMnpNNC40IDE3LjZsMy4zLTguOCAzLjMgNi42IDIuMi0zLjIgNC40IDUuNEg0LjR6Ii8+Cjwvc3ZnPgo=);
    --jp-icon-info: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDUwLjk3OCA1MC45NzgiPgoJPGcgY2xhc3M9ImpwLWljb24zIiBmaWxsPSIjNjE2MTYxIj4KCQk8cGF0aCBkPSJNNDMuNTIsNy40NThDMzguNzExLDIuNjQ4LDMyLjMwNywwLDI1LjQ4OSwwQzE4LjY3LDAsMTIuMjY2LDIuNjQ4LDcuNDU4LDcuNDU4CgkJCWMtOS45NDMsOS45NDEtOS45NDMsMjYuMTE5LDAsMzYuMDYyYzQuODA5LDQuODA5LDExLjIxMiw3LjQ1NiwxOC4wMzEsNy40NThjMCwwLDAuMDAxLDAsMC4wMDIsMAoJCQljNi44MTYsMCwxMy4yMjEtMi42NDgsMTguMDI5LTcuNDU4YzQuODA5LTQuODA5LDcuNDU3LTExLjIxMiw3LjQ1Ny0xOC4wM0M1MC45NzcsMTguNjcsNDguMzI4LDEyLjI2Niw0My41Miw3LjQ1OHoKCQkJIE00Mi4xMDYsNDIuMTA1Yy00LjQzMiw0LjQzMS0xMC4zMzIsNi44NzItMTYuNjE1LDYuODcyaC0wLjAwMmMtNi4yODUtMC4wMDEtMTIuMTg3LTIuNDQxLTE2LjYxNy02Ljg3MgoJCQljLTkuMTYyLTkuMTYzLTkuMTYyLTI0LjA3MSwwLTMzLjIzM0MxMy4zMDMsNC40NCwxOS4yMDQsMiwyNS40ODksMmM2LjI4NCwwLDEyLjE4NiwyLjQ0LDE2LjYxNyw2Ljg3MgoJCQljNC40MzEsNC40MzEsNi44NzEsMTAuMzMyLDYuODcxLDE2LjYxN0M0OC45NzcsMzEuNzcyLDQ2LjUzNiwzNy42NzUsNDIuMTA2LDQyLjEwNXoiLz4KCQk8cGF0aCBkPSJNMjMuNTc4LDMyLjIxOGMtMC4wMjMtMS43MzQsMC4xNDMtMy4wNTksMC40OTYtMy45NzJjMC4zNTMtMC45MTMsMS4xMS0xLjk5NywyLjI3Mi0zLjI1MwoJCQljMC40NjgtMC41MzYsMC45MjMtMS4wNjIsMS4zNjctMS41NzVjMC42MjYtMC43NTMsMS4xMDQtMS40NzgsMS40MzYtMi4xNzVjMC4zMzEtMC43MDcsMC40OTUtMS41NDEsMC40OTUtMi41CgkJCWMwLTEuMDk2LTAuMjYtMi4wODgtMC43NzktMi45NzljLTAuNTY1LTAuODc5LTEuNTAxLTEuMzM2LTIuODA2LTEuMzY5Yy0xLjgwMiwwLjA1Ny0yLjk4NSwwLjY2Ny0zLjU1LDEuODMyCgkJCWMtMC4zMDEsMC41MzUtMC41MDMsMS4xNDEtMC42MDcsMS44MTRjLTAuMTM5LDAuNzA3LTAuMjA3LDEuNDMyLTAuMjA3LDIuMTc0aC0yLjkzN2MtMC4wOTEtMi4yMDgsMC40MDctNC4xMTQsMS40OTMtNS43MTkKCQkJYzEuMDYyLTEuNjQsMi44NTUtMi40ODEsNS4zNzgtMi41MjdjMi4xNiwwLjAyMywzLjg3NCwwLjYwOCw1LjE0MSwxLjc1OGMxLjI3OCwxLjE2LDEuOTI5LDIuNzY0LDEuOTUsNC44MTEKCQkJYzAsMS4xNDItMC4xMzcsMi4xMTEtMC40MSwyLjkxMWMtMC4zMDksMC44NDUtMC43MzEsMS41OTMtMS4yNjgsMi4yNDNjLTAuNDkyLDAuNjUtMS4wNjgsMS4zMTgtMS43MywyLjAwMgoJCQljLTAuNjUsMC42OTctMS4zMTMsMS40NzktMS45ODcsMi4zNDZjLTAuMjM5LDAuMzc3LTAuNDI5LDAuNzc3LTAuNTY1LDEuMTk5Yy0wLjE2LDAuOTU5LTAuMjE3LDEuOTUxLTAuMTcxLDIuOTc5CgkJCUMyNi41ODksMzIuMjE4LDIzLjU3OCwzMi4yMTgsMjMuNTc4LDMyLjIxOHogTTIzLjU3OCwzOC4yMnYtMy40ODRoMy4wNzZ2My40ODRIMjMuNTc4eiIvPgoJPC9nPgo8L3N2Zz4K);
    --jp-icon-inspector: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaW5zcGVjdG9yLWljb24tY29sb3IganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMjAgNEg0Yy0xLjEgMC0xLjk5LjktMS45OSAyTDIgMThjMCAxLjEuOSAyIDIgMmgxNmMxLjEgMCAyLS45IDItMlY2YzAtMS4xLS45LTItMi0yem0tNSAxNEg0di00aDExdjR6bTAtNUg0VjloMTF2NHptNSA1aC00VjloNHY5eiIvPgo8L3N2Zz4K);
    --jp-icon-json: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtanNvbi1pY29uLWNvbG9yIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iI0Y5QTgyNSI+CiAgICA8cGF0aCBkPSJNMjAuMiAxMS44Yy0xLjYgMC0xLjcuNS0xLjcgMSAwIC40LjEuOS4xIDEuMy4xLjUuMS45LjEgMS4zIDAgMS43LTEuNCAyLjMtMy41IDIuM2gtLjl2LTEuOWguNWMxLjEgMCAxLjQgMCAxLjQtLjggMC0uMyAwLS42LS4xLTEgMC0uNC0uMS0uOC0uMS0xLjIgMC0xLjMgMC0xLjggMS4zLTItMS4zLS4yLTEuMy0uNy0xLjMtMiAwLS40LjEtLjguMS0xLjIuMS0uNC4xLS43LjEtMSAwLS44LS40LS43LTEuNC0uOGgtLjVWNC4xaC45YzIuMiAwIDMuNS43IDMuNSAyLjMgMCAuNC0uMS45LS4xIDEuMy0uMS41LS4xLjktLjEgMS4zIDAgLjUuMiAxIDEuNyAxdjEuOHpNMS44IDEwLjFjMS42IDAgMS43LS41IDEuNy0xIDAtLjQtLjEtLjktLjEtMS4zLS4xLS41LS4xLS45LS4xLTEuMyAwLTEuNiAxLjQtMi4zIDMuNS0yLjNoLjl2MS45aC0uNWMtMSAwLTEuNCAwLTEuNC44IDAgLjMgMCAuNi4xIDEgMCAuMi4xLjYuMSAxIDAgMS4zIDAgMS44LTEuMyAyQzYgMTEuMiA2IDExLjcgNiAxM2MwIC40LS4xLjgtLjEgMS4yLS4xLjMtLjEuNy0uMSAxIDAgLjguMy44IDEuNC44aC41djEuOWgtLjljLTIuMSAwLTMuNS0uNi0zLjUtMi4zIDAtLjQuMS0uOS4xLTEuMy4xLS41LjEtLjkuMS0xLjMgMC0uNS0uMi0xLTEuNy0xdi0xLjl6Ii8+CiAgICA8Y2lyY2xlIGN4PSIxMSIgY3k9IjEzLjgiIHI9IjIuMSIvPgogICAgPGNpcmNsZSBjeD0iMTEiIGN5PSI4LjIiIHI9IjIuMSIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-julia: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDMyNSAzMDAiPgogIDxnIGNsYXNzPSJqcC1icmFuZDAganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjY2IzYzMzIj4KICAgIDxwYXRoIGQ9Ik0gMTUwLjg5ODQzOCAyMjUgQyAxNTAuODk4NDM4IDI2Ni40MjE4NzUgMTE3LjMyMDMxMiAzMDAgNzUuODk4NDM4IDMwMCBDIDM0LjQ3NjU2MiAzMDAgMC44OTg0MzggMjY2LjQyMTg3NSAwLjg5ODQzOCAyMjUgQyAwLjg5ODQzOCAxODMuNTc4MTI1IDM0LjQ3NjU2MiAxNTAgNzUuODk4NDM4IDE1MCBDIDExNy4zMjAzMTIgMTUwIDE1MC44OTg0MzggMTgzLjU3ODEyNSAxNTAuODk4NDM4IDIyNSIvPgogIDwvZz4KICA8ZyBjbGFzcz0ianAtYnJhbmQwIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iIzM4OTgyNiI+CiAgICA8cGF0aCBkPSJNIDIzNy41IDc1IEMgMjM3LjUgMTE2LjQyMTg3NSAyMDMuOTIxODc1IDE1MCAxNjIuNSAxNTAgQyAxMjEuMDc4MTI1IDE1MCA4Ny41IDExNi40MjE4NzUgODcuNSA3NSBDIDg3LjUgMzMuNTc4MTI1IDEyMS4wNzgxMjUgMCAxNjIuNSAwIEMgMjAzLjkyMTg3NSAwIDIzNy41IDMzLjU3ODEyNSAyMzcuNSA3NSIvPgogIDwvZz4KICA8ZyBjbGFzcz0ianAtYnJhbmQwIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iIzk1NThiMiI+CiAgICA8cGF0aCBkPSJNIDMyNC4xMDE1NjIgMjI1IEMgMzI0LjEwMTU2MiAyNjYuNDIxODc1IDI5MC41MjM0MzggMzAwIDI0OS4xMDE1NjIgMzAwIEMgMjA3LjY3OTY4OCAzMDAgMTc0LjEwMTU2MiAyNjYuNDIxODc1IDE3NC4xMDE1NjIgMjI1IEMgMTc0LjEwMTU2MiAxODMuNTc4MTI1IDIwNy42Nzk2ODggMTUwIDI0OS4xMDE1NjIgMTUwIEMgMjkwLjUyMzQzOCAxNTAgMzI0LjEwMTU2MiAxODMuNTc4MTI1IDMyNC4xMDE1NjIgMjI1Ii8+CiAgPC9nPgo8L3N2Zz4K);
    --jp-icon-jupyter-favicon: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTUyIiBoZWlnaHQ9IjE2NSIgdmlld0JveD0iMCAwIDE1MiAxNjUiIHZlcnNpb249IjEuMSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgPGcgY2xhc3M9ImpwLWp1cHl0ZXItaWNvbi1jb2xvciIgZmlsbD0iI0YzNzcyNiI+CiAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgwLjA3ODk0NywgMTEwLjU4MjkyNykiIGQ9Ik03NS45NDIyODQyLDI5LjU4MDQ1NjEgQzQzLjMwMjM5NDcsMjkuNTgwNDU2MSAxNC43OTY3ODMyLDE3LjY1MzQ2MzQgMCwwIEM1LjUxMDgzMjExLDE1Ljg0MDY4MjkgMTUuNzgxNTM4OSwyOS41NjY3NzMyIDI5LjM5MDQ5NDcsMzkuMjc4NDE3MSBDNDIuOTk5Nyw0OC45ODk4NTM3IDU5LjI3MzcsNTQuMjA2NzgwNSA3NS45NjA1Nzg5LDU0LjIwNjc4MDUgQzkyLjY0NzQ1NzksNTQuMjA2NzgwNSAxMDguOTIxNDU4LDQ4Ljk4OTg1MzcgMTIyLjUzMDY2MywzOS4yNzg0MTcxIEMxMzYuMTM5NDUzLDI5LjU2Njc3MzIgMTQ2LjQxMDI4NCwxNS44NDA2ODI5IDE1MS45MjExNTgsMCBDMTM3LjA4Nzg2OCwxNy42NTM0NjM0IDEwOC41ODI1ODksMjkuNTgwNDU2MSA3NS45NDIyODQyLDI5LjU4MDQ1NjEgTDc1Ljk0MjI4NDIsMjkuNTgwNDU2MSBaIiAvPgogICAgPHBhdGggdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMC4wMzczNjgsIDAuNzA0ODc4KSIgZD0iTTc1Ljk3ODQ1NzksMjQuNjI2NDA3MyBDMTA4LjYxODc2MywyNC42MjY0MDczIDEzNy4xMjQ0NTgsMzYuNTUzNDQxNSAxNTEuOTIxMTU4LDU0LjIwNjc4MDUgQzE0Ni40MTAyODQsMzguMzY2MjIyIDEzNi4xMzk0NTMsMjQuNjQwMTMxNyAxMjIuNTMwNjYzLDE0LjkyODQ4NzggQzEwOC45MjE0NTgsNS4yMTY4NDM5IDkyLjY0NzQ1NzksMCA3NS45NjA1Nzg5LDAgQzU5LjI3MzcsMCA0Mi45OTk3LDUuMjE2ODQzOSAyOS4zOTA0OTQ3LDE0LjkyODQ4NzggQzE1Ljc4MTUzODksMjQuNjQwMTMxNyA1LjUxMDgzMjExLDM4LjM2NjIyMiAwLDU0LjIwNjc4MDUgQzE0LjgzMzA4MTYsMzYuNTg5OTI5MyA0My4zMzg1Njg0LDI0LjYyNjQwNzMgNzUuOTc4NDU3OSwyNC42MjY0MDczIEw3NS45Nzg0NTc5LDI0LjYyNjQwNzMgWiIgLz4KICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-jupyter: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMzkiIGhlaWdodD0iNTEiIHZpZXdCb3g9IjAgMCAzOSA1MSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgtMTYzOCAtMjI4MSkiPgogICAgIDxnIGNsYXNzPSJqcC1qdXB5dGVyLWljb24tY29sb3IiIGZpbGw9IiNGMzc3MjYiPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjM5Ljc0IDIzMTEuOTgpIiBkPSJNIDE4LjI2NDYgNy4xMzQxMUMgMTAuNDE0NSA3LjEzNDExIDMuNTU4NzIgNC4yNTc2IDAgMEMgMS4zMjUzOSAzLjgyMDQgMy43OTU1NiA3LjEzMDgxIDcuMDY4NiA5LjQ3MzAzQyAxMC4zNDE3IDExLjgxNTIgMTQuMjU1NyAxMy4wNzM0IDE4LjI2OSAxMy4wNzM0QyAyMi4yODIzIDEzLjA3MzQgMjYuMTk2MyAxMS44MTUyIDI5LjQ2OTQgOS40NzMwM0MgMzIuNzQyNCA3LjEzMDgxIDM1LjIxMjYgMy44MjA0IDM2LjUzOCAwQyAzMi45NzA1IDQuMjU3NiAyNi4xMTQ4IDcuMTM0MTEgMTguMjY0NiA3LjEzNDExWiIvPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjM5LjczIDIyODUuNDgpIiBkPSJNIDE4LjI3MzMgNS45MzkzMUMgMjYuMTIzNSA1LjkzOTMxIDMyLjk3OTMgOC44MTU4MyAzNi41MzggMTMuMDczNEMgMzUuMjEyNiA5LjI1MzAzIDMyLjc0MjQgNS45NDI2MiAyOS40Njk0IDMuNjAwNEMgMjYuMTk2MyAxLjI1ODE4IDIyLjI4MjMgMCAxOC4yNjkgMEMgMTQuMjU1NyAwIDEwLjM0MTcgMS4yNTgxOCA3LjA2ODYgMy42MDA0QyAzLjc5NTU2IDUuOTQyNjIgMS4zMjUzOSA5LjI1MzAzIDAgMTMuMDczNEMgMy41Njc0NSA4LjgyNDYzIDEwLjQyMzIgNS45MzkzMSAxOC4yNzMzIDUuOTM5MzFaIi8+CiAgICA8L2c+CiAgICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjY5LjMgMjI4MS4zMSkiIGQ9Ik0gNS44OTM1MyAyLjg0NEMgNS45MTg4OSAzLjQzMTY1IDUuNzcwODUgNC4wMTM2NyA1LjQ2ODE1IDQuNTE2NDVDIDUuMTY1NDUgNS4wMTkyMiA0LjcyMTY4IDUuNDIwMTUgNC4xOTI5OSA1LjY2ODUxQyAzLjY2NDMgNS45MTY4OCAzLjA3NDQ0IDYuMDAxNTEgMi40OTgwNSA1LjkxMTcxQyAxLjkyMTY2IDUuODIxOSAxLjM4NDYzIDUuNTYxNyAwLjk1NDg5OCA1LjE2NDAxQyAwLjUyNTE3IDQuNzY2MzMgMC4yMjIwNTYgNC4yNDkwMyAwLjA4MzkwMzcgMy42Nzc1N0MgLTAuMDU0MjQ4MyAzLjEwNjExIC0wLjAyMTIzIDIuNTA2MTcgMC4xNzg3ODEgMS45NTM2NEMgMC4zNzg3OTMgMS40MDExIDAuNzM2ODA5IDAuOTIwODE3IDEuMjA3NTQgMC41NzM1MzhDIDEuNjc4MjYgMC4yMjYyNTkgMi4yNDA1NSAwLjAyNzU5MTkgMi44MjMyNiAwLjAwMjY3MjI5QyAzLjYwMzg5IC0wLjAzMDcxMTUgNC4zNjU3MyAwLjI0OTc4OSA0Ljk0MTQyIDAuNzgyNTUxQyA1LjUxNzExIDEuMzE1MzEgNS44NTk1NiAyLjA1Njc2IDUuODkzNTMgMi44NDRaIi8+CiAgICAgIDxwYXRoIHRyYW5zZm9ybT0idHJhbnNsYXRlKDE2MzkuOCAyMzIzLjgxKSIgZD0iTSA3LjQyNzg5IDMuNTgzMzhDIDcuNDYwMDggNC4zMjQzIDcuMjczNTUgNS4wNTgxOSA2Ljg5MTkzIDUuNjkyMTNDIDYuNTEwMzEgNi4zMjYwNyA1Ljk1MDc1IDYuODMxNTYgNS4yODQxMSA3LjE0NDZDIDQuNjE3NDcgNy40NTc2MyAzLjg3MzcxIDcuNTY0MTQgMy4xNDcwMiA3LjQ1MDYzQyAyLjQyMDMyIDcuMzM3MTIgMS43NDMzNiA3LjAwODcgMS4yMDE4NCA2LjUwNjk1QyAwLjY2MDMyOCA2LjAwNTIgMC4yNzg2MSA1LjM1MjY4IDAuMTA1MDE3IDQuNjMyMDJDIC0wLjA2ODU3NTcgMy45MTEzNSAtMC4wMjYyMzYxIDMuMTU0OTQgMC4yMjY2NzUgMi40NTg1NkMgMC40Nzk1ODcgMS43NjIxNyAwLjkzMTY5NyAxLjE1NzEzIDEuNTI1NzYgMC43MjAwMzNDIDIuMTE5ODMgMC4yODI5MzUgMi44MjkxNCAwLjAzMzQzOTUgMy41NjM4OSAwLjAwMzEzMzQ0QyA0LjU0NjY3IC0wLjAzNzQwMzMgNS41MDUyOSAwLjMxNjcwNiA2LjIyOTYxIDAuOTg3ODM1QyA2Ljk1MzkzIDEuNjU4OTYgNy4zODQ4NCAyLjU5MjM1IDcuNDI3ODkgMy41ODMzOEwgNy40Mjc4OSAzLjU4MzM4WiIvPgogICAgICA8cGF0aCB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxNjM4LjM2IDIyODYuMDYpIiBkPSJNIDIuMjc0NzEgNC4zOTYyOUMgMS44NDM2MyA0LjQxNTA4IDEuNDE2NzEgNC4zMDQ0NSAxLjA0Nzk5IDQuMDc4NDNDIDAuNjc5MjY4IDMuODUyNCAwLjM4NTMyOCAzLjUyMTE0IDAuMjAzMzcxIDMuMTI2NTZDIDAuMDIxNDEzNiAyLjczMTk4IC0wLjA0MDM3OTggMi4yOTE4MyAwLjAyNTgxMTYgMS44NjE4MUMgMC4wOTIwMDMxIDEuNDMxOCAwLjI4MzIwNCAxLjAzMTI2IDAuNTc1MjEzIDAuNzEwODgzQyAwLjg2NzIyMiAwLjM5MDUxIDEuMjQ2OTEgMC4xNjQ3MDggMS42NjYyMiAwLjA2MjA1OTJDIDIuMDg1NTMgLTAuMDQwNTg5NyAyLjUyNTYxIC0wLjAxNTQ3MTQgMi45MzA3NiAwLjEzNDIzNUMgMy4zMzU5MSAwLjI4Mzk0MSAzLjY4NzkyIDAuNTUxNTA1IDMuOTQyMjIgMC45MDMwNkMgNC4xOTY1MiAxLjI1NDYyIDQuMzQxNjkgMS42NzQzNiA0LjM1OTM1IDIuMTA5MTZDIDQuMzgyOTkgMi42OTEwNyA0LjE3Njc4IDMuMjU4NjkgMy43ODU5NyAzLjY4NzQ2QyAzLjM5NTE2IDQuMTE2MjQgMi44NTE2NiA0LjM3MTE2IDIuMjc0NzEgNC4zOTYyOUwgMi4yNzQ3MSA0LjM5NjI5WiIvPgogICAgPC9nPgogIDwvZz4+Cjwvc3ZnPgo=);
    --jp-icon-jupyterlab-wordmark: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyMDAiIHZpZXdCb3g9IjAgMCAxODYwLjggNDc1Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiM0RTRFNEUiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDQ4MC4xMzY0MDEsIDY0LjI3MTQ5MykiPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMC4wMDAwMDAsIDU4Ljg3NTU2NikiPgogICAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgwLjA4NzYwMywgMC4xNDAyOTQpIj4KICAgICAgICA8cGF0aCBkPSJNLTQyNi45LDE2OS44YzAsNDguNy0zLjcsNjQuNy0xMy42LDc2LjRjLTEwLjgsMTAtMjUsMTUuNS0zOS43LDE1LjVsMy43LDI5IGMyMi44LDAuMyw0NC44LTcuOSw2MS45LTIzLjFjMTcuOC0xOC41LDI0LTQ0LjEsMjQtODMuM1YwSC00Mjd2MTcwLjFMLTQyNi45LDE2OS44TC00MjYuOSwxNjkuOHoiLz4KICAgICAgPC9nPgogICAgPC9nPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMTU1LjA0NTI5NiwgNTYuODM3MTA0KSI+CiAgICAgIDxnIHRyYW5zZm9ybT0idHJhbnNsYXRlKDEuNTYyNDUzLCAxLjc5OTg0MikiPgogICAgICAgIDxwYXRoIGQ9Ik0tMzEyLDE0OGMwLDIxLDAsMzkuNSwxLjcsNTUuNGgtMzEuOGwtMi4xLTMzLjNoLTAuOGMtNi43LDExLjYtMTYuNCwyMS4zLTI4LDI3LjkgYy0xMS42LDYuNi0yNC44LDEwLTM4LjIsOS44Yy0zMS40LDAtNjktMTcuNy02OS04OVYwaDM2LjR2MTEyLjdjMCwzOC43LDExLjYsNjQuNyw0NC42LDY0LjdjMTAuMy0wLjIsMjAuNC0zLjUsMjguOS05LjQgYzguNS01LjksMTUuMS0xNC4zLDE4LjktMjMuOWMyLjItNi4xLDMuMy0xMi41LDMuMy0xOC45VjAuMmgzNi40VjE0OEgtMzEyTC0zMTIsMTQ4eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgzOTAuMDEzMzIyLCA1My40Nzk2MzgpIj4KICAgICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMS43MDY0NTgsIDAuMjMxNDI1KSI+CiAgICAgICAgPHBhdGggZD0iTS00NzguNiw3MS40YzAtMjYtMC44LTQ3LTEuNy02Ni43aDMyLjdsMS43LDM0LjhoMC44YzcuMS0xMi41LDE3LjUtMjIuOCwzMC4xLTI5LjcgYzEyLjUtNywyNi43LTEwLjMsNDEtOS44YzQ4LjMsMCw4NC43LDQxLjcsODQuNywxMDMuM2MwLDczLjEtNDMuNywxMDkuMi05MSwxMDkuMmMtMTIuMSwwLjUtMjQuMi0yLjItMzUtNy44IGMtMTAuOC01LjYtMTkuOS0xMy45LTI2LjYtMjQuMmgtMC44VjI5MWgtMzZ2LTIyMEwtNDc4LjYsNzEuNEwtNDc4LjYsNzEuNHogTS00NDIuNiwxMjUuNmMwLjEsNS4xLDAuNiwxMC4xLDEuNywxNS4xIGMzLDEyLjMsOS45LDIzLjMsMTkuOCwzMS4xYzkuOSw3LjgsMjIuMSwxMi4xLDM0LjcsMTIuMWMzOC41LDAsNjAuNy0zMS45LDYwLjctNzguNWMwLTQwLjctMjEuMS03NS42LTU5LjUtNzUuNiBjLTEyLjksMC40LTI1LjMsNS4xLTM1LjMsMTMuNGMtOS45LDguMy0xNi45LDE5LjctMTkuNiwzMi40Yy0xLjUsNC45LTIuMywxMC0yLjUsMTUuMVYxMjUuNkwtNDQyLjYsMTI1LjZMLTQ0Mi42LDEyNS42eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSg2MDYuNzQwNzI2LCA1Ni44MzcxMDQpIj4KICAgICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMC43NTEyMjYsIDEuOTg5Mjk5KSI+CiAgICAgICAgPHBhdGggZD0iTS00NDAuOCwwbDQzLjcsMTIwLjFjNC41LDEzLjQsOS41LDI5LjQsMTIuOCw0MS43aDAuOGMzLjctMTIuMiw3LjktMjcuNywxMi44LTQyLjQgbDM5LjctMTE5LjJoMzguNUwtMzQ2LjksMTQ1Yy0yNiw2OS43LTQzLjcsMTA1LjQtNjguNiwxMjcuMmMtMTIuNSwxMS43LTI3LjksMjAtNDQuNiwyMy45bC05LjEtMzEuMSBjMTEuNy0zLjksMjIuNS0xMC4xLDMxLjgtMTguMWMxMy4yLTExLjEsMjMuNy0yNS4yLDMwLjYtNDEuMmMxLjUtMi44LDIuNS01LjcsMi45LTguOGMtMC4zLTMuMy0xLjItNi42LTIuNS05LjdMLTQ4MC4yLDAuMSBoMzkuN0wtNDQwLjgsMEwtNDQwLjgsMHoiLz4KICAgICAgPC9nPgogICAgPC9nPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoODIyLjc0ODEwNCwgMC4wMDAwMDApIj4KICAgICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMS40NjQwNTAsIDAuMzc4OTE0KSI+CiAgICAgICAgPHBhdGggZD0iTS00MTMuNywwdjU4LjNoNTJ2MjguMmgtNTJWMTk2YzAsMjUsNywzOS41LDI3LjMsMzkuNWM3LjEsMC4xLDE0LjItMC43LDIxLjEtMi41IGwxLjcsMjcuN2MtMTAuMywzLjctMjEuMyw1LjQtMzIuMiw1Yy03LjMsMC40LTE0LjYtMC43LTIxLjMtMy40Yy02LjgtMi43LTEyLjktNi44LTE3LjktMTIuMWMtMTAuMy0xMC45LTE0LjEtMjktMTQuMS01Mi45IFY4Ni41aC0zMVY1OC4zaDMxVjkuNkwtNDEzLjcsMEwtNDEzLjcsMHoiLz4KICAgICAgPC9nPgogICAgPC9nPgogICAgPGcgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoOTc0LjQzMzI4NiwgNTMuNDc5NjM4KSI+CiAgICAgIDxnIHRyYW5zZm9ybT0idHJhbnNsYXRlKDAuOTkwMDM0LCAwLjYxMDMzOSkiPgogICAgICAgIDxwYXRoIGQ9Ik0tNDQ1LjgsMTEzYzAuOCw1MCwzMi4yLDcwLjYsNjguNiw3MC42YzE5LDAuNiwzNy45LTMsNTUuMy0xMC41bDYuMiwyNi40IGMtMjAuOSw4LjktNDMuNSwxMy4xLTY2LjIsMTIuNmMtNjEuNSwwLTk4LjMtNDEuMi05OC4zLTEwMi41Qy00ODAuMiw0OC4yLTQ0NC43LDAtMzg2LjUsMGM2NS4yLDAsODIuNyw1OC4zLDgyLjcsOTUuNyBjLTAuMSw1LjgtMC41LDExLjUtMS4yLDE3LjJoLTE0MC42SC00NDUuOEwtNDQ1LjgsMTEzeiBNLTMzOS4yLDg2LjZjMC40LTIzLjUtOS41LTYwLjEtNTAuNC02MC4xIGMtMzYuOCwwLTUyLjgsMzQuNC01NS43LDYwLjFILTMzOS4yTC0zMzkuMiw4Ni42TC0zMzkuMiw4Ni42eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgICA8ZyB0cmFuc2Zvcm09InRyYW5zbGF0ZSgxMjAxLjk2MTA1OCwgNTMuNDc5NjM4KSI+CiAgICAgIDxnIHRyYW5zZm9ybT0idHJhbnNsYXRlKDEuMTc5NjQwLCAwLjcwNTA2OCkiPgogICAgICAgIDxwYXRoIGQ9Ik0tNDc4LjYsNjhjMC0yMy45LTAuNC00NC41LTEuNy02My40aDMxLjhsMS4yLDM5LjloMS43YzkuMS0yNy4zLDMxLTQ0LjUsNTUuMy00NC41IGMzLjUtMC4xLDcsMC40LDEwLjMsMS4ydjM0LjhjLTQuMS0wLjktOC4yLTEuMy0xMi40LTEuMmMtMjUuNiwwLTQzLjcsMTkuNy00OC43LDQ3LjRjLTEsNS43LTEuNiwxMS41LTEuNywxNy4ydjEwOC4zaC0zNlY2OCBMLTQ3OC42LDY4eiIvPgogICAgICA8L2c+CiAgICA8L2c+CiAgPC9nPgoKICA8ZyBjbGFzcz0ianAtaWNvbi13YXJuMCIgZmlsbD0iI0YzNzcyNiI+CiAgICA8cGF0aCBkPSJNMTM1Mi4zLDMyNi4yaDM3VjI4aC0zN1YzMjYuMnogTTE2MDQuOCwzMjYuMmMtMi41LTEzLjktMy40LTMxLjEtMy40LTQ4Ljd2LTc2IGMwLTQwLjctMTUuMS04My4xLTc3LjMtODMuMWMtMjUuNiwwLTUwLDcuMS02Ni44LDE4LjFsOC40LDI0LjRjMTQuMy05LjIsMzQtMTUuMSw1My0xNS4xYzQxLjYsMCw0Ni4yLDMwLjIsNDYuMiw0N3Y0LjIgYy03OC42LTAuNC0xMjIuMywyNi41LTEyMi4zLDc1LjZjMCwyOS40LDIxLDU4LjQsNjIuMiw1OC40YzI5LDAsNTAuOS0xNC4zLDYyLjItMzAuMmgxLjNsMi45LDI1LjZIMTYwNC44eiBNMTU2NS43LDI1Ny43IGMwLDMuOC0wLjgsOC0yLjEsMTEuOGMtNS45LDE3LjItMjIuNywzNC00OS4yLDM0Yy0xOC45LDAtMzQuOS0xMS4zLTM0LjktMzUuM2MwLTM5LjUsNDUuOC00Ni42LDg2LjItNDUuOFYyNTcuN3ogTTE2OTguNSwzMjYuMiBsMS43LTMzLjZoMS4zYzE1LjEsMjYuOSwzOC43LDM4LjIsNjguMSwzOC4yYzQ1LjQsMCw5MS4yLTM2LjEsOTEuMi0xMDguOGMwLjQtNjEuNy0zNS4zLTEwMy43LTg1LjctMTAzLjcgYy0zMi44LDAtNTYuMywxNC43LTY5LjMsMzcuNGgtMC44VjI4aC0zNi42djI0NS43YzAsMTguMS0wLjgsMzguNi0xLjcsNTIuNUgxNjk4LjV6IE0xNzA0LjgsMjA4LjJjMC01LjksMS4zLTEwLjksMi4xLTE1LjEgYzcuNi0yOC4xLDMxLjEtNDUuNCw1Ni4zLTQ1LjRjMzkuNSwwLDYwLjUsMzQuOSw2MC41LDc1LjZjMCw0Ni42LTIzLjEsNzguMS02MS44LDc4LjFjLTI2LjksMC00OC4zLTE3LjYtNTUuNS00My4zIGMtMC44LTQuMi0xLjctOC44LTEuNy0xMy40VjIwOC4yeiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-kernel: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgZmlsbD0iIzYxNjE2MSIgZD0iTTE1IDlIOXY2aDZWOXptLTIgNGgtMnYtMmgydjJ6bTgtMlY5aC0yVjdjMC0xLjEtLjktMi0yLTJoLTJWM2gtMnYyaC0yVjNIOXYySDdjLTEuMSAwLTIgLjktMiAydjJIM3YyaDJ2MkgzdjJoMnYyYzAgMS4xLjkgMiAyIDJoMnYyaDJ2LTJoMnYyaDJ2LTJoMmMxLjEgMCAyLS45IDItMnYtMmgydi0yaC0ydi0yaDJ6bS00IDZIN1Y3aDEwdjEweiIvPgo8L3N2Zz4K);
    --jp-icon-keyboard: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMjAgNUg0Yy0xLjEgMC0xLjk5LjktMS45OSAyTDIgMTdjMCAxLjEuOSAyIDIgMmgxNmMxLjEgMCAyLS45IDItMlY3YzAtMS4xLS45LTItMi0yem0tOSAzaDJ2MmgtMlY4em0wIDNoMnYyaC0ydi0yek04IDhoMnYySDhWOHptMCAzaDJ2Mkg4di0yem0tMSAySDV2LTJoMnYyem0wLTNINVY4aDJ2MnptOSA3SDh2LTJoOHYyem0wLTRoLTJ2LTJoMnYyem0wLTNoLTJWOGgydjJ6bTMgM2gtMnYtMmgydjJ6bTAtM2gtMlY4aDJ2MnoiLz4KPC9zdmc+Cg==);
    --jp-icon-launch: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMzIgMzIiIHdpZHRoPSIzMiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxwYXRoIGQ9Ik0yNiwyOEg2YTIuMDAyNywyLjAwMjcsMCwwLDEtMi0yVjZBMi4wMDI3LDIuMDAyNywwLDAsMSw2LDRIMTZWNkg2VjI2SDI2VjE2aDJWMjZBMi4wMDI3LDIuMDAyNywwLDAsMSwyNiwyOFoiLz4KICAgIDxwb2x5Z29uIHBvaW50cz0iMjAgMiAyMCA0IDI2LjU4NiA0IDE4IDEyLjU4NiAxOS40MTQgMTQgMjggNS40MTQgMjggMTIgMzAgMTIgMzAgMiAyMCAyIi8+CiAgPC9nPgo8L3N2Zz4K);
    --jp-icon-launcher: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTkgMTlINVY1aDdWM0g1YTIgMiAwIDAwLTIgMnYxNGEyIDIgMCAwMDIgMmgxNGMxLjEgMCAyLS45IDItMnYtN2gtMnY3ek0xNCAzdjJoMy41OWwtOS44MyA5LjgzIDEuNDEgMS40MUwxOSA2LjQxVjEwaDJWM2gtN3oiLz4KPC9zdmc+Cg==);
    --jp-icon-line-form: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxwYXRoIGZpbGw9IndoaXRlIiBkPSJNNS44OCA0LjEyTDEzLjc2IDEybC03Ljg4IDcuODhMOCAyMmwxMC0xMEw4IDJ6Ii8+Cjwvc3ZnPgo=);
    --jp-icon-link: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTMuOSAxMmMwLTEuNzEgMS4zOS0zLjEgMy4xLTMuMWg0VjdIN2MtMi43NiAwLTUgMi4yNC01IDVzMi4yNCA1IDUgNWg0di0xLjlIN2MtMS43MSAwLTMuMS0xLjM5LTMuMS0zLjF6TTggMTNoOHYtMkg4djJ6bTktNmgtNHYxLjloNGMxLjcxIDAgMy4xIDEuMzkgMy4xIDMuMXMtMS4zOSAzLjEtMy4xIDMuMWgtNFYxN2g0YzIuNzYgMCA1LTIuMjQgNS01cy0yLjI0LTUtNS01eiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-list: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiM2MTYxNjEiIGQ9Ik0xOSA1djE0SDVWNWgxNG0xLjEtMkgzLjljLS41IDAtLjkuNC0uOS45djE2LjJjMCAuNC40LjkuOS45aDE2LjJjLjQgMCAuOS0uNS45LS45VjMuOWMwLS41LS41LS45LS45LS45ek0xMSA3aDZ2MmgtNlY3em0wIDRoNnYyaC02di0yem0wIDRoNnYyaC02ek03IDdoMnYySDd6bTAgNGgydjJIN3ptMCA0aDJ2Mkg3eiIvPgo8L3N2Zz4K);
    --jp-icon-markdown: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1jb250cmFzdDAganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjN0IxRkEyIiBkPSJNNSAxNC45aDEybC02LjEgNnptOS40LTYuOGMwLTEuMy0uMS0yLjktLjEtNC41LS40IDEuNC0uOSAyLjktMS4zIDQuM2wtMS4zIDQuM2gtMkw4LjUgNy45Yy0uNC0xLjMtLjctMi45LTEtNC4zLS4xIDEuNi0uMSAzLjItLjIgNC42TDcgMTIuNEg0LjhsLjctMTFoMy4zTDEwIDVjLjQgMS4yLjcgMi43IDEgMy45LjMtMS4yLjctMi42IDEtMy45bDEuMi0zLjdoMy4zbC42IDExaC0yLjRsLS4zLTQuMnoiLz4KPC9zdmc+Cg==);
    --jp-icon-move-down: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTQiIGhlaWdodD0iMTQiIHZpZXdCb3g9IjAgMCAxNCAxNCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KPHBhdGggY2xhc3M9ImpwLWljb24zIiBkPSJNMTIuNDcxIDcuNTI4OTlDMTIuNzYzMiA3LjIzNjg0IDEyLjc2MzIgNi43NjMxNiAxMi40NzEgNi40NzEwMVY2LjQ3MTAxQzEyLjE3OSA2LjE3OTA1IDExLjcwNTcgNi4xNzg4NCAxMS40MTM1IDYuNDcwNTRMNy43NSAxMC4xMjc1VjEuNzVDNy43NSAxLjMzNTc5IDcuNDE0MjEgMSA3IDFWMUM2LjU4NTc5IDEgNi4yNSAxLjMzNTc5IDYuMjUgMS43NVYxMC4xMjc1TDIuNTk3MjYgNi40NjgyMkMyLjMwMzM4IDYuMTczODEgMS44MjY0MSA2LjE3MzU5IDEuNTMyMjYgNi40Njc3NFY2LjQ2Nzc0QzEuMjM4MyA2Ljc2MTcgMS4yMzgzIDcuMjM4MyAxLjUzMjI2IDcuNTMyMjZMNi4yOTI4OSAxMi4yOTI5QzYuNjgzNDIgMTIuNjgzNCA3LjMxNjU4IDEyLjY4MzQgNy43MDcxMSAxMi4yOTI5TDEyLjQ3MSA3LjUyODk5WiIgZmlsbD0iIzYxNjE2MSIvPgo8L3N2Zz4K);
    --jp-icon-move-up: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTQiIGhlaWdodD0iMTQiIHZpZXdCb3g9IjAgMCAxNCAxNCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KPHBhdGggY2xhc3M9ImpwLWljb24zIiBkPSJNMS41Mjg5OSA2LjQ3MTAxQzEuMjM2ODQgNi43NjMxNiAxLjIzNjg0IDcuMjM2ODQgMS41Mjg5OSA3LjUyODk5VjcuNTI4OTlDMS44MjA5NSA3LjgyMDk1IDIuMjk0MjYgNy44MjExNiAyLjU4NjQ5IDcuNTI5NDZMNi4yNSAzLjg3MjVWMTIuMjVDNi4yNSAxMi42NjQyIDYuNTg1NzkgMTMgNyAxM1YxM0M3LjQxNDIxIDEzIDcuNzUgMTIuNjY0MiA3Ljc1IDEyLjI1VjMuODcyNUwxMS40MDI3IDcuNTMxNzhDMTEuNjk2NiA3LjgyNjE5IDEyLjE3MzYgNy44MjY0MSAxMi40Njc3IDcuNTMyMjZWNy41MzIyNkMxMi43NjE3IDcuMjM4MyAxMi43NjE3IDYuNzYxNyAxMi40Njc3IDYuNDY3NzRMNy43MDcxMSAxLjcwNzExQzcuMzE2NTggMS4zMTY1OCA2LjY4MzQyIDEuMzE2NTggNi4yOTI4OSAxLjcwNzExTDEuNTI4OTkgNi40NzEwMVoiIGZpbGw9IiM2MTYxNjEiLz4KPC9zdmc+Cg==);
    --jp-icon-new-folder: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTIwIDZoLThsLTItMkg0Yy0xLjExIDAtMS45OS44OS0xLjk5IDJMMiAxOGMwIDEuMTEuODkgMiAyIDJoMTZjMS4xMSAwIDItLjg5IDItMlY4YzAtMS4xMS0uODktMi0yLTJ6bS0xIDhoLTN2M2gtMnYtM2gtM3YtMmgzVjloMnYzaDN2MnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-not-trusted: url(data:image/svg+xml;base64,PHN2ZyBmaWxsPSJub25lIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI1IDI1Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgc3Ryb2tlPSIjMzMzMzMzIiBzdHJva2Utd2lkdGg9IjIiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDMgMykiIGQ9Ik0xLjg2MDk0IDExLjQ0MDlDMC44MjY0NDggOC43NzAyNyAwLjg2Mzc3OSA2LjA1NzY0IDEuMjQ5MDcgNC4xOTkzMkMyLjQ4MjA2IDMuOTMzNDcgNC4wODA2OCAzLjQwMzQ3IDUuNjAxMDIgMi44NDQ5QzcuMjM1NDkgMi4yNDQ0IDguODU2NjYgMS41ODE1IDkuOTg3NiAxLjA5NTM5QzExLjA1OTcgMS41ODM0MSAxMi42MDk0IDIuMjQ0NCAxNC4yMTggMi44NDMzOUMxNS43NTAzIDMuNDEzOTQgMTcuMzk5NSAzLjk1MjU4IDE4Ljc1MzkgNC4yMTM4NUMxOS4xMzY0IDYuMDcxNzcgMTkuMTcwOSA4Ljc3NzIyIDE4LjEzOSAxMS40NDA5QzE3LjAzMDMgMTQuMzAzMiAxNC42NjY4IDE3LjE4NDQgOS45OTk5OSAxOC45MzU0QzUuMzMzMTkgMTcuMTg0NCAyLjk2OTY4IDE0LjMwMzIgMS44NjA5NCAxMS40NDA5WiIvPgogICAgPHBhdGggY2xhc3M9ImpwLWljb24yIiBzdHJva2U9IiMzMzMzMzMiIHN0cm9rZS13aWR0aD0iMiIgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoOS4zMTU5MiA5LjMyMDMxKSIgZD0iTTcuMzY4NDIgMEwwIDcuMzY0NzkiLz4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgc3Ryb2tlPSIjMzMzMzMzIiBzdHJva2Utd2lkdGg9IjIiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDkuMzE1OTIgMTYuNjgzNikgc2NhbGUoMSAtMSkiIGQ9Ik03LjM2ODQyIDBMMCA3LjM2NDc5Ii8+Cjwvc3ZnPgo=);
    --jp-icon-notebook: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtbm90ZWJvb2staWNvbi1jb2xvciBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiNFRjZDMDAiPgogICAgPHBhdGggZD0iTTE4LjcgMy4zdjE1LjRIMy4zVjMuM2gxNS40bTEuNS0xLjVIMS44djE4LjNoMTguM2wuMS0xOC4zeiIvPgogICAgPHBhdGggZD0iTTE2LjUgMTYuNWwtNS40LTQuMy01LjYgNC4zdi0xMWgxMXoiLz4KICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-numbering: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjIiIGhlaWdodD0iMjIiIHZpZXdCb3g9IjAgMCAyOCAyOCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CgkJPHBhdGggZD0iTTQgMTlINlYxOS41SDVWMjAuNUg2VjIxSDRWMjJIN1YxOEg0VjE5Wk01IDEwSDZWNkg0VjdINVYxMFpNNCAxM0g1LjhMNCAxNS4xVjE2SDdWMTVINS4yTDcgMTIuOVYxMkg0VjEzWk05IDdWOUgyM1Y3SDlaTTkgMjFIMjNWMTlIOVYyMVpNOSAxNUgyM1YxM0g5VjE1WiIvPgoJPC9nPgo8L3N2Zz4K);
    --jp-icon-offline-bolt: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCIgd2lkdGg9IjE2Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyIDIuMDJjLTUuNTEgMC05Ljk4IDQuNDctOS45OCA5Ljk4czQuNDcgOS45OCA5Ljk4IDkuOTggOS45OC00LjQ3IDkuOTgtOS45OFMxNy41MSAyLjAyIDEyIDIuMDJ6TTExLjQ4IDIwdi02LjI2SDhMMTMgNHY2LjI2aDMuMzVMMTEuNDggMjB6Ii8+CiAgPC9nPgo8L3N2Zz4K);
    --jp-icon-palette: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE4IDEzVjIwSDRWNkg5LjAyQzkuMDcgNS4yOSA5LjI0IDQuNjIgOS41IDRINEMyLjkgNCAyIDQuOSAyIDZWMjBDMiAyMS4xIDIuOSAyMiA0IDIySDE4QzE5LjEgMjIgMjAgMjEuMSAyMCAyMFYxNUwxOCAxM1pNMTkuMyA4Ljg5QzE5Ljc0IDguMTkgMjAgNy4zOCAyMCA2LjVDMjAgNC4wMSAxNy45OSAyIDE1LjUgMkMxMy4wMSAyIDExIDQuMDEgMTEgNi41QzExIDguOTkgMTMuMDEgMTEgMTUuNDkgMTFDMTYuMzcgMTEgMTcuMTkgMTAuNzQgMTcuODggMTAuM0wyMSAxMy40MkwyMi40MiAxMkwxOS4zIDguODlaTTE1LjUgOUMxNC4xMiA5IDEzIDcuODggMTMgNi41QzEzIDUuMTIgMTQuMTIgNCAxNS41IDRDMTYuODggNCAxOCA1LjEyIDE4IDYuNUMxOCA3Ljg4IDE2Ljg4IDkgMTUuNSA5WiIvPgogICAgPHBhdGggZmlsbC1ydWxlPSJldmVub2RkIiBjbGlwLXJ1bGU9ImV2ZW5vZGQiIGQ9Ik00IDZIOS4wMTg5NEM5LjAwNjM5IDYuMTY1MDIgOSA2LjMzMTc2IDkgNi41QzkgOC44MTU3NyAxMC4yMTEgMTAuODQ4NyAxMi4wMzQzIDEySDlWMTRIMTZWMTIuOTgxMUMxNi41NzAzIDEyLjkzNzcgMTcuMTIgMTIuODIwNyAxNy42Mzk2IDEyLjYzOTZMMTggMTNWMjBINFY2Wk04IDhINlYxMEg4VjhaTTYgMTJIOFYxNEg2VjEyWk04IDE2SDZWMThIOFYxNlpNOSAxNkgxNlYxOEg5VjE2WiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-paste: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTE5IDJoLTQuMThDMTQuNC44NCAxMy4zIDAgMTIgMGMtMS4zIDAtMi40Ljg0LTIuODIgMkg1Yy0xLjEgMC0yIC45LTIgMnYxNmMwIDEuMS45IDIgMiAyaDE0YzEuMSAwIDItLjkgMi0yVjRjMC0xLjEtLjktMi0yLTJ6bS03IDBjLjU1IDAgMSAuNDUgMSAxcy0uNDUgMS0xIDEtMS0uNDUtMS0xIC40NS0xIDEtMXptNyAxOEg1VjRoMnYzaDEwVjRoMnYxNnoiLz4KICAgIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-pdf: url(data:image/svg+xml;base64,PHN2ZwogICB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyMiAyMiIgd2lkdGg9IjE2Ij4KICAgIDxwYXRoIHRyYW5zZm9ybT0icm90YXRlKDQ1KSIgY2xhc3M9ImpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iI0ZGMkEyQSIKICAgICAgIGQ9Im0gMjIuMzQ0MzY5LC0zLjAxNjM2NDIgaCA1LjYzODYwNCB2IDEuNTc5MjQzMyBoIC0zLjU0OTIyNyB2IDEuNTA4NjkyOTkgaCAzLjMzNzU3NiBWIDEuNjUwODE1NCBoIC0zLjMzNzU3NiB2IDMuNDM1MjYxMyBoIC0yLjA4OTM3NyB6IG0gLTcuMTM2NDQ0LDEuNTc5MjQzMyB2IDQuOTQzOTU0MyBoIDAuNzQ4OTIgcSAxLjI4MDc2MSwwIDEuOTUzNzAzLC0wLjYzNDk1MzUgMC42NzgzNjksLTAuNjM0OTUzNSAwLjY3ODM2OSwtMS44NDUxNjQxIDAsLTEuMjA0NzgzNTUgLTAuNjcyOTQyLC0xLjgzNDMxMDExIC0wLjY3Mjk0MiwtMC42Mjk1MjY1OSAtMS45NTkxMywtMC42Mjk1MjY1OSB6IG0gLTIuMDg5Mzc3LC0xLjU3OTI0MzMgaCAyLjIwMzM0MyBxIDEuODQ1MTY0LDAgMi43NDYwMzksMC4yNjU5MjA3IDAuOTA2MzAxLDAuMjYwNDkzNyAxLjU1MjEwOCwwLjg5MDAyMDMgMC41Njk4MywwLjU0ODEyMjMgMC44NDY2MDUsMS4yNjQ0ODAwNiAwLjI3Njc3NCwwLjcxNjM1NzgxIDAuMjc2Nzc0LDEuNjIyNjU4OTQgMCwwLjkxNzE1NTEgLTAuMjc2Nzc0LDEuNjM4OTM5OSAtMC4yNzY3NzUsMC43MTYzNTc4IC0wLjg0NjYwNSwxLjI2NDQ4IC0wLjY1MTIzNCwwLjYyOTUyNjYgLTEuNTYyOTYyLDAuODk1NDQ3MyAtMC45MTE3MjgsMC4yNjA0OTM3IC0yLjczNTE4NSwwLjI2MDQ5MzcgaCAtMi4yMDMzNDMgeiBtIC04LjE0NTg1NjUsMCBoIDMuNDY3ODIzIHEgMS41NDY2ODE2LDAgMi4zNzE1Nzg1LDAuNjg5MjIzIDAuODMwMzI0LDAuNjgzNzk2MSAwLjgzMDMyNCwxLjk1MzcwMzE0IDAsMS4yNzUzMzM5NyAtMC44MzAzMjQsMS45NjQ1NTcwNiBRIDkuOTg3MTk2MSwyLjI3NDkxNSA4LjQ0MDUxNDUsMi4yNzQ5MTUgSCA3LjA2MjA2ODQgViA1LjA4NjA3NjcgSCA0Ljk3MjY5MTUgWiBtIDIuMDg5Mzc2OSwxLjUxNDExOTkgdiAyLjI2MzAzOTQzIGggMS4xNTU5NDEgcSAwLjYwNzgxODgsMCAwLjkzODg2MjksLTAuMjkzMDU1NDcgMC4zMzEwNDQxLC0wLjI5ODQ4MjQxIDAuMzMxMDQ0MSwtMC44NDExNzc3MiAwLC0wLjU0MjY5NTMxIC0wLjMzMTA0NDEsLTAuODM1NzUwNzQgLTAuMzMxMDQ0MSwtMC4yOTMwNTU1IC0wLjkzODg2MjksLTAuMjkzMDU1NSB6IgovPgo8L3N2Zz4K);
    --jp-icon-python: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iLTEwIC0xMCAxMzEuMTYxMzYxNjk0MzM1OTQgMTMyLjM4ODk5OTkzODk2NDg0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjMzA2OTk4IiBkPSJNIDU0LjkxODc4NSw5LjE5Mjc0MjFlLTQgQyA1MC4zMzUxMzIsMC4wMjIyMTcyNyA0NS45NTc4NDYsMC40MTMxMzY5NyA0Mi4xMDYyODUsMS4wOTQ2NjkzIDMwLjc2MDA2OSwzLjA5OTE3MzEgMjguNzAwMDM2LDcuMjk0NzcxNCAyOC43MDAwMzUsMTUuMDMyMTY5IHYgMTAuMjE4NzUgaCAyNi44MTI1IHYgMy40MDYyNSBoIC0yNi44MTI1IC0xMC4wNjI1IGMgLTcuNzkyNDU5LDAgLTE0LjYxNTc1ODgsNC42ODM3MTcgLTE2Ljc0OTk5OTgsMTMuNTkzNzUgLTIuNDYxODE5OTgsMTAuMjEyOTY2IC0yLjU3MTAxNTA4LDE2LjU4NjAyMyAwLDI3LjI1IDEuOTA1OTI4Myw3LjkzNzg1MiA2LjQ1NzU0MzIsMTMuNTkzNzQ4IDE0LjI0OTk5OTgsMTMuNTkzNzUgaCA5LjIxODc1IHYgLTEyLjI1IGMgMCwtOC44NDk5MDIgNy42NTcxNDQsLTE2LjY1NjI0OCAxNi43NSwtMTYuNjU2MjUgaCAyNi43ODEyNSBjIDcuNDU0OTUxLDAgMTMuNDA2MjUzLC02LjEzODE2NCAxMy40MDYyNSwtMTMuNjI1IHYgLTI1LjUzMTI1IGMgMCwtNy4yNjYzMzg2IC02LjEyOTk4LC0xMi43MjQ3NzcxIC0xMy40MDYyNSwtMTMuOTM3NDk5NyBDIDY0LjI4MTU0OCwwLjMyNzk0Mzk3IDU5LjUwMjQzOCwtMC4wMjAzNzkwMyA1NC45MTg3ODUsOS4xOTI3NDIxZS00IFogbSAtMTQuNSw4LjIxODc1MDEyNTc5IGMgMi43Njk1NDcsMCA1LjAzMTI1LDIuMjk4NjQ1NiA1LjAzMTI1LDUuMTI0OTk5NiAtMmUtNiwyLjgxNjMzNiAtMi4yNjE3MDMsNS4wOTM3NSAtNS4wMzEyNSw1LjA5Mzc1IC0yLjc3OTQ3NiwtMWUtNiAtNS4wMzEyNSwtMi4yNzc0MTUgLTUuMDMxMjUsLTUuMDkzNzUgLTEwZS03LC0yLjgyNjM1MyAyLjI1MTc3NCwtNS4xMjQ5OTk2IDUuMDMxMjUsLTUuMTI0OTk5NiB6Ii8+CiAgPHBhdGggY2xhc3M9ImpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iI2ZmZDQzYiIgZD0ibSA4NS42Mzc1MzUsMjguNjU3MTY5IHYgMTEuOTA2MjUgYyAwLDkuMjMwNzU1IC03LjgyNTg5NSwxNi45OTk5OTkgLTE2Ljc1LDE3IGggLTI2Ljc4MTI1IGMgLTcuMzM1ODMzLDAgLTEzLjQwNjI0OSw2LjI3ODQ4MyAtMTMuNDA2MjUsMTMuNjI1IHYgMjUuNTMxMjQ3IGMgMCw3LjI2NjM0NCA2LjMxODU4OCwxMS41NDAzMjQgMTMuNDA2MjUsMTMuNjI1MDA0IDguNDg3MzMxLDIuNDk1NjEgMTYuNjI2MjM3LDIuOTQ2NjMgMjYuNzgxMjUsMCA2Ljc1MDE1NSwtMS45NTQzOSAxMy40MDYyNTMsLTUuODg3NjEgMTMuNDA2MjUsLTEzLjYyNTAwNCBWIDg2LjUwMDkxOSBoIC0yNi43ODEyNSB2IC0zLjQwNjI1IGggMjYuNzgxMjUgMTMuNDA2MjU0IGMgNy43OTI0NjEsMCAxMC42OTYyNTEsLTUuNDM1NDA4IDEzLjQwNjI0MSwtMTMuNTkzNzUgMi43OTkzMywtOC4zOTg4ODYgMi42ODAyMiwtMTYuNDc1Nzc2IDAsLTI3LjI1IC0xLjkyNTc4LC03Ljc1NzQ0MSAtNS42MDM4NywtMTMuNTkzNzUgLTEzLjQwNjI0MSwtMTMuNTkzNzUgeiBtIC0xNS4wNjI1LDY0LjY1NjI1IGMgMi43Nzk0NzgsM2UtNiA1LjAzMTI1LDIuMjc3NDE3IDUuMDMxMjUsNS4wOTM3NDcgLTJlLTYsMi44MjYzNTQgLTIuMjUxNzc1LDUuMTI1MDA0IC01LjAzMTI1LDUuMTI1MDA0IC0yLjc2OTU1LDAgLTUuMDMxMjUsLTIuMjk4NjUgLTUuMDMxMjUsLTUuMTI1MDA0IDJlLTYsLTIuODE2MzMgMi4yNjE2OTcsLTUuMDkzNzQ3IDUuMDMxMjUsLTUuMDkzNzQ3IHoiLz4KPC9zdmc+Cg==);
    --jp-icon-r-kernel: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1jb250cmFzdDMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjMjE5NkYzIiBkPSJNNC40IDIuNWMxLjItLjEgMi45LS4zIDQuOS0uMyAyLjUgMCA0LjEuNCA1LjIgMS4zIDEgLjcgMS41IDEuOSAxLjUgMy41IDAgMi0xLjQgMy41LTIuOSA0LjEgMS4yLjQgMS43IDEuNiAyLjIgMyAuNiAxLjkgMSAzLjkgMS4zIDQuNmgtMy44Yy0uMy0uNC0uOC0xLjctMS4yLTMuN3MtMS4yLTIuNi0yLjYtMi42aC0uOXY2LjRINC40VjIuNXptMy43IDYuOWgxLjRjMS45IDAgMi45LS45IDIuOS0yLjNzLTEtMi4zLTIuOC0yLjNjLS43IDAtMS4zIDAtMS42LjJ2NC41aC4xdi0uMXoiLz4KPC9zdmc+Cg==);
    --jp-icon-react: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMTUwIDE1MCA1NDEuOSAyOTUuMyI+CiAgPGcgY2xhc3M9ImpwLWljb24tYnJhbmQyIGpwLWljb24tc2VsZWN0YWJsZSIgZmlsbD0iIzYxREFGQiI+CiAgICA8cGF0aCBkPSJNNjY2LjMgMjk2LjVjMC0zMi41LTQwLjctNjMuMy0xMDMuMS04Mi40IDE0LjQtNjMuNiA4LTExNC4yLTIwLjItMTMwLjQtNi41LTMuOC0xNC4xLTUuNi0yMi40LTUuNnYyMi4zYzQuNiAwIDguMy45IDExLjQgMi42IDEzLjYgNy44IDE5LjUgMzcuNSAxNC45IDc1LjctMS4xIDkuNC0yLjkgMTkuMy01LjEgMjkuNC0xOS42LTQuOC00MS04LjUtNjMuNS0xMC45LTEzLjUtMTguNS0yNy41LTM1LjMtNDEuNi01MCAzMi42LTMwLjMgNjMuMi00Ni45IDg0LTQ2LjlWNzhjLTI3LjUgMC02My41IDE5LjYtOTkuOSA1My42LTM2LjQtMzMuOC03Mi40LTUzLjItOTkuOS01My4ydjIyLjNjMjAuNyAwIDUxLjQgMTYuNSA4NCA0Ni42LTE0IDE0LjctMjggMzEuNC00MS4zIDQ5LjktMjIuNiAyLjQtNDQgNi4xLTYzLjYgMTEtMi4zLTEwLTQtMTkuNy01LjItMjktNC43LTM4LjIgMS4xLTY3LjkgMTQuNi03NS44IDMtMS44IDYuOS0yLjYgMTEuNS0yLjZWNzguNWMtOC40IDAtMTYgMS44LTIyLjYgNS42LTI4LjEgMTYuMi0zNC40IDY2LjctMTkuOSAxMzAuMS02Mi4yIDE5LjItMTAyLjcgNDkuOS0xMDIuNyA4Mi4zIDAgMzIuNSA0MC43IDYzLjMgMTAzLjEgODIuNC0xNC40IDYzLjYtOCAxMTQuMiAyMC4yIDEzMC40IDYuNSAzLjggMTQuMSA1LjYgMjIuNSA1LjYgMjcuNSAwIDYzLjUtMTkuNiA5OS45LTUzLjYgMzYuNCAzMy44IDcyLjQgNTMuMiA5OS45IDUzLjIgOC40IDAgMTYtMS44IDIyLjYtNS42IDI4LjEtMTYuMiAzNC40LTY2LjcgMTkuOS0xMzAuMSA2Mi0xOS4xIDEwMi41LTQ5LjkgMTAyLjUtODIuM3ptLTEzMC4yLTY2LjdjLTMuNyAxMi45LTguMyAyNi4yLTEzLjUgMzkuNS00LjEtOC04LjQtMTYtMTMuMS0yNC00LjYtOC05LjUtMTUuOC0xNC40LTIzLjQgMTQuMiAyLjEgMjcuOSA0LjcgNDEgNy45em0tNDUuOCAxMDYuNWMtNy44IDEzLjUtMTUuOCAyNi4zLTI0LjEgMzguMi0xNC45IDEuMy0zMCAyLTQ1LjIgMi0xNS4xIDAtMzAuMi0uNy00NS0xLjktOC4zLTExLjktMTYuNC0yNC42LTI0LjItMzgtNy42LTEzLjEtMTQuNS0yNi40LTIwLjgtMzkuOCA2LjItMTMuNCAxMy4yLTI2LjggMjAuNy0zOS45IDcuOC0xMy41IDE1LjgtMjYuMyAyNC4xLTM4LjIgMTQuOS0xLjMgMzAtMiA0NS4yLTIgMTUuMSAwIDMwLjIuNyA0NSAxLjkgOC4zIDExLjkgMTYuNCAyNC42IDI0LjIgMzggNy42IDEzLjEgMTQuNSAyNi40IDIwLjggMzkuOC02LjMgMTMuNC0xMy4yIDI2LjgtMjAuNyAzOS45em0zMi4zLTEzYzUuNCAxMy40IDEwIDI2LjggMTMuOCAzOS44LTEzLjEgMy4yLTI2LjkgNS45LTQxLjIgOCA0LjktNy43IDkuOC0xNS42IDE0LjQtMjMuNyA0LjYtOCA4LjktMTYuMSAxMy0yNC4xek00MjEuMiA0MzBjLTkuMy05LjYtMTguNi0yMC4zLTI3LjgtMzIgOSAuNCAxOC4yLjcgMjcuNS43IDkuNCAwIDE4LjctLjIgMjcuOC0uNy05IDExLjctMTguMyAyMi40LTI3LjUgMzJ6bS03NC40LTU4LjljLTE0LjItMi4xLTI3LjktNC43LTQxLTcuOSAzLjctMTIuOSA4LjMtMjYuMiAxMy41LTM5LjUgNC4xIDggOC40IDE2IDEzLjEgMjQgNC43IDggOS41IDE1LjggMTQuNCAyMy40ek00MjAuNyAxNjNjOS4zIDkuNiAxOC42IDIwLjMgMjcuOCAzMi05LS40LTE4LjItLjctMjcuNS0uNy05LjQgMC0xOC43LjItMjcuOC43IDktMTEuNyAxOC4zLTIyLjQgMjcuNS0zMnptLTc0IDU4LjljLTQuOSA3LjctOS44IDE1LjYtMTQuNCAyMy43LTQuNiA4LTguOSAxNi0xMyAyNC01LjQtMTMuNC0xMC0yNi44LTEzLjgtMzkuOCAxMy4xLTMuMSAyNi45LTUuOCA0MS4yLTcuOXptLTkwLjUgMTI1LjJjLTM1LjQtMTUuMS01OC4zLTM0LjktNTguMy01MC42IDAtMTUuNyAyMi45LTM1LjYgNTguMy01MC42IDguNi0zLjcgMTgtNyAyNy43LTEwLjEgNS43IDE5LjYgMTMuMiA0MCAyMi41IDYwLjktOS4yIDIwLjgtMTYuNiA0MS4xLTIyLjIgNjAuNi05LjktMy4xLTE5LjMtNi41LTI4LTEwLjJ6TTMxMCA0OTBjLTEzLjYtNy44LTE5LjUtMzcuNS0xNC45LTc1LjcgMS4xLTkuNCAyLjktMTkuMyA1LjEtMjkuNCAxOS42IDQuOCA0MSA4LjUgNjMuNSAxMC45IDEzLjUgMTguNSAyNy41IDM1LjMgNDEuNiA1MC0zMi42IDMwLjMtNjMuMiA0Ni45LTg0IDQ2LjktNC41LS4xLTguMy0xLTExLjMtMi43em0yMzcuMi03Ni4yYzQuNyAzOC4yLTEuMSA2Ny45LTE0LjYgNzUuOC0zIDEuOC02LjkgMi42LTExLjUgMi42LTIwLjcgMC01MS40LTE2LjUtODQtNDYuNiAxNC0xNC43IDI4LTMxLjQgNDEuMy00OS45IDIyLjYtMi40IDQ0LTYuMSA2My42LTExIDIuMyAxMC4xIDQuMSAxOS44IDUuMiAyOS4xem0zOC41LTY2LjdjLTguNiAzLjctMTggNy0yNy43IDEwLjEtNS43LTE5LjYtMTMuMi00MC0yMi41LTYwLjkgOS4yLTIwLjggMTYuNi00MS4xIDIyLjItNjAuNiA5LjkgMy4xIDE5LjMgNi41IDI4LjEgMTAuMiAzNS40IDE1LjEgNTguMyAzNC45IDU4LjMgNTAuNi0uMSAxNS43LTIzIDM1LjYtNTguNCA1MC42ek0zMjAuOCA3OC40eiIvPgogICAgPGNpcmNsZSBjeD0iNDIwLjkiIGN5PSIyOTYuNSIgcj0iNDUuNyIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-redo: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIGhlaWdodD0iMjQiIHZpZXdCb3g9IjAgMCAyNCAyNCIgd2lkdGg9IjE2Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgICA8cGF0aCBkPSJNMCAwaDI0djI0SDB6IiBmaWxsPSJub25lIi8+PHBhdGggZD0iTTE4LjQgMTAuNkMxNi41NSA4Ljk5IDE0LjE1IDggMTEuNSA4Yy00LjY1IDAtOC41OCAzLjAzLTkuOTYgNy4yMkwzLjkgMTZjMS4wNS0zLjE5IDQuMDUtNS41IDcuNi01LjUgMS45NSAwIDMuNzMuNzIgNS4xMiAxLjg4TDEzIDE2aDlWN2wtMy42IDMuNnoiLz4KICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-refresh: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDE4IDE4Ij4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTkgMTMuNWMtMi40OSAwLTQuNS0yLjAxLTQuNS00LjVTNi41MSA0LjUgOSA0LjVjMS4yNCAwIDIuMzYuNTIgMy4xNyAxLjMzTDEwIDhoNVYzbC0xLjc2IDEuNzZDMTIuMTUgMy42OCAxMC42NiAzIDkgMyA1LjY5IDMgMy4wMSA1LjY5IDMuMDEgOVM1LjY5IDE1IDkgMTVjMi45NyAwIDUuNDMtMi4xNiA1LjktNWgtMS41MmMtLjQ2IDItMi4yNCAzLjUtNC4zOCAzLjV6Ii8+CiAgICA8L2c+Cjwvc3ZnPgo=);
    --jp-icon-regex: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KICA8ZyBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiM0MTQxNDEiPgogICAgPHJlY3QgeD0iMiIgeT0iMiIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2Ii8+CiAgPC9nPgoKICA8ZyBjbGFzcz0ianAtaWNvbi1hY2NlbnQyIiBmaWxsPSIjRkZGIj4KICAgIDxjaXJjbGUgY2xhc3M9InN0MiIgY3g9IjUuNSIgY3k9IjE0LjUiIHI9IjEuNSIvPgogICAgPHJlY3QgeD0iMTIiIHk9IjQiIGNsYXNzPSJzdDIiIHdpZHRoPSIxIiBoZWlnaHQ9IjgiLz4KICAgIDxyZWN0IHg9IjguNSIgeT0iNy41IiB0cmFuc2Zvcm09Im1hdHJpeCgwLjg2NiAtMC41IDAuNSAwLjg2NiAtMi4zMjU1IDcuMzIxOSkiIGNsYXNzPSJzdDIiIHdpZHRoPSI4IiBoZWlnaHQ9IjEiLz4KICAgIDxyZWN0IHg9IjEyIiB5PSI0IiB0cmFuc2Zvcm09Im1hdHJpeCgwLjUgLTAuODY2IDAuODY2IDAuNSAtMC42Nzc5IDE0LjgyNTIpIiBjbGFzcz0ic3QyIiB3aWR0aD0iMSIgaGVpZ2h0PSI4Ii8+CiAgPC9nPgo8L3N2Zz4K);
    --jp-icon-run: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTggNXYxNGwxMS03eiIvPgogICAgPC9nPgo8L3N2Zz4K);
    --jp-icon-running: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDUxMiA1MTIiPgogIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICA8cGF0aCBkPSJNMjU2IDhDMTE5IDggOCAxMTkgOCAyNTZzMTExIDI0OCAyNDggMjQ4IDI0OC0xMTEgMjQ4LTI0OFMzOTMgOCAyNTYgOHptOTYgMzI4YzAgOC44LTcuMiAxNi0xNiAxNkgxNzZjLTguOCAwLTE2LTcuMi0xNi0xNlYxNzZjMC04LjggNy4yLTE2IDE2LTE2aDE2MGM4LjggMCAxNiA3LjIgMTYgMTZ2MTYweiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-save: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTE3IDNINWMtMS4xMSAwLTIgLjktMiAydjE0YzAgMS4xLjg5IDIgMiAyaDE0YzEuMSAwIDItLjkgMi0yVjdsLTQtNHptLTUgMTZjLTEuNjYgMC0zLTEuMzQtMy0zczEuMzQtMyAzLTMgMyAxLjM0IDMgMy0xLjM0IDMtMyAzem0zLTEwSDVWNWgxMHY0eiIvPgogICAgPC9nPgo8L3N2Zz4K);
    --jp-icon-search: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMTggMTgiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyLjEsMTAuOWgtMC43bC0wLjItMC4yYzAuOC0wLjksMS4zLTIuMiwxLjMtMy41YzAtMy0yLjQtNS40LTUuNC01LjRTMS44LDQuMiwxLjgsNy4xczIuNCw1LjQsNS40LDUuNCBjMS4zLDAsMi41LTAuNSwzLjUtMS4zbDAuMiwwLjJ2MC43bDQuMSw0LjFsMS4yLTEuMkwxMi4xLDEwLjl6IE03LjEsMTAuOWMtMi4xLDAtMy43LTEuNy0zLjctMy43czEuNy0zLjcsMy43LTMuN3MzLjcsMS43LDMuNywzLjcgUzkuMiwxMC45LDcuMSwxMC45eiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-settings: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIiBkPSJNMTkuNDMgMTIuOThjLjA0LS4zMi4wNy0uNjQuMDctLjk4cy0uMDMtLjY2LS4wNy0uOThsMi4xMS0xLjY1Yy4xOS0uMTUuMjQtLjQyLjEyLS42NGwtMi0zLjQ2Yy0uMTItLjIyLS4zOS0uMy0uNjEtLjIybC0yLjQ5IDFjLS41Mi0uNC0xLjA4LS43My0xLjY5LS45OGwtLjM4LTIuNjVBLjQ4OC40ODggMCAwMDE0IDJoLTRjLS4yNSAwLS40Ni4xOC0uNDkuNDJsLS4zOCAyLjY1Yy0uNjEuMjUtMS4xNy41OS0xLjY5Ljk4bC0yLjQ5LTFjLS4yMy0uMDktLjQ5IDAtLjYxLjIybC0yIDMuNDZjLS4xMy4yMi0uMDcuNDkuMTIuNjRsMi4xMSAxLjY1Yy0uMDQuMzItLjA3LjY1LS4wNy45OHMuMDMuNjYuMDcuOThsLTIuMTEgMS42NWMtLjE5LjE1LS4yNC40Mi0uMTIuNjRsMiAzLjQ2Yy4xMi4yMi4zOS4zLjYxLjIybDIuNDktMWMuNTIuNCAxLjA4LjczIDEuNjkuOThsLjM4IDIuNjVjLjAzLjI0LjI0LjQyLjQ5LjQyaDRjLjI1IDAgLjQ2LS4xOC40OS0uNDJsLjM4LTIuNjVjLjYxLS4yNSAxLjE3LS41OSAxLjY5LS45OGwyLjQ5IDFjLjIzLjA5LjQ5IDAgLjYxLS4yMmwyLTMuNDZjLjEyLS4yMi4wNy0uNDktLjEyLS42NGwtMi4xMS0xLjY1ek0xMiAxNS41Yy0xLjkzIDAtMy41LTEuNTctMy41LTMuNXMxLjU3LTMuNSAzLjUtMy41IDMuNSAxLjU3IDMuNSAzLjUtMS41NyAzLjUtMy41IDMuNXoiLz4KPC9zdmc+Cg==);
    --jp-icon-share: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIHZpZXdCb3g9IjAgMCAyNCAyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTSAxOCAyIEMgMTYuMzU0OTkgMiAxNSAzLjM1NDk5MDQgMTUgNSBDIDE1IDUuMTkwOTUyOSAxNS4wMjE3OTEgNS4zNzcxMjI0IDE1LjA1NjY0MSA1LjU1ODU5MzggTCA3LjkyMTg3NSA5LjcyMDcwMzEgQyA3LjM5ODUzOTkgOS4yNzc4NTM5IDYuNzMyMDc3MSA5IDYgOSBDIDQuMzU0OTkwNCA5IDMgMTAuMzU0OTkgMyAxMiBDIDMgMTMuNjQ1MDEgNC4zNTQ5OTA0IDE1IDYgMTUgQyA2LjczMjA3NzEgMTUgNy4zOTg1Mzk5IDE0LjcyMjE0NiA3LjkyMTg3NSAxNC4yNzkyOTcgTCAxNS4wNTY2NDEgMTguNDM5NDUzIEMgMTUuMDIxNTU1IDE4LjYyMTUxNCAxNSAxOC44MDgzODYgMTUgMTkgQyAxNSAyMC42NDUwMSAxNi4zNTQ5OSAyMiAxOCAyMiBDIDE5LjY0NTAxIDIyIDIxIDIwLjY0NTAxIDIxIDE5IEMgMjEgMTcuMzU0OTkgMTkuNjQ1MDEgMTYgMTggMTYgQyAxNy4yNjc0OCAxNiAxNi42MDE1OTMgMTYuMjc5MzI4IDE2LjA3ODEyNSAxNi43MjI2NTYgTCA4Ljk0MzM1OTQgMTIuNTU4NTk0IEMgOC45NzgyMDk1IDEyLjM3NzEyMiA5IDEyLjE5MDk1MyA5IDEyIEMgOSAxMS44MDkwNDcgOC45NzgyMDk1IDExLjYyMjg3OCA4Ljk0MzM1OTQgMTEuNDQxNDA2IEwgMTYuMDc4MTI1IDcuMjc5Mjk2OSBDIDE2LjYwMTQ2IDcuNzIyMTQ2MSAxNy4yNjc5MjMgOCAxOCA4IEMgMTkuNjQ1MDEgOCAyMSA2LjY0NTAwOTYgMjEgNSBDIDIxIDMuMzU0OTkwNCAxOS42NDUwMSAyIDE4IDIgeiBNIDE4IDQgQyAxOC41NjQxMjkgNCAxOSA0LjQzNTg3MDYgMTkgNSBDIDE5IDUuNTY0MTI5NCAxOC41NjQxMjkgNiAxOCA2IEMgMTcuNDM1ODcxIDYgMTcgNS41NjQxMjk0IDE3IDUgQyAxNyA0LjQzNTg3MDYgMTcuNDM1ODcxIDQgMTggNCB6IE0gNiAxMSBDIDYuNTY0MTI5NCAxMSA3IDExLjQzNTg3MSA3IDEyIEMgNyAxMi41NjQxMjkgNi41NjQxMjk0IDEzIDYgMTMgQyA1LjQzNTg3MDYgMTMgNSAxMi41NjQxMjkgNSAxMiBDIDUgMTEuNDM1ODcxIDUuNDM1ODcwNiAxMSA2IDExIHogTSAxOCAxOCBDIDE4LjU2NDEyOSAxOCAxOSAxOC40MzU4NzEgMTkgMTkgQyAxOSAxOS41NjQxMjkgMTguNTY0MTI5IDIwIDE4IDIwIEMgMTcuNDM1ODcxIDIwIDE3IDE5LjU2NDEyOSAxNyAxOSBDIDE3IDE4LjQzNTg3MSAxNy40MzU4NzEgMTggMTggMTggeiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-spreadsheet: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8cGF0aCBjbGFzcz0ianAtaWNvbi1jb250cmFzdDEganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNENBRjUwIiBkPSJNMi4yIDIuMnYxNy42aDE3LjZWMi4ySDIuMnptMTUuNCA3LjdoLTUuNVY0LjRoNS41djUuNXpNOS45IDQuNHY1LjVINC40VjQuNGg1LjV6bS01LjUgNy43aDUuNXY1LjVINC40di01LjV6bTcuNyA1LjV2LTUuNWg1LjV2NS41aC01LjV6Ii8+Cjwvc3ZnPgo=);
    --jp-icon-stop: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTAgMGgyNHYyNEgweiIgZmlsbD0ibm9uZSIvPgogICAgICAgIDxwYXRoIGQ9Ik02IDZoMTJ2MTJINnoiLz4KICAgIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-tab: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTIxIDNIM2MtMS4xIDAtMiAuOS0yIDJ2MTRjMCAxLjEuOSAyIDIgMmgxOGMxLjEgMCAyLS45IDItMlY1YzAtMS4xLS45LTItMi0yem0wIDE2SDNWNWgxMHY0aDh2MTB6Ii8+CiAgPC9nPgo8L3N2Zz4K);
    --jp-icon-table-rows: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTAgMGgyNHYyNEgweiIgZmlsbD0ibm9uZSIvPgogICAgICAgIDxwYXRoIGQ9Ik0yMSw4SDNWNGgxOFY4eiBNMjEsMTBIM3Y0aDE4VjEweiBNMjEsMTZIM3Y0aDE4VjE2eiIvPgogICAgPC9nPgo8L3N2Zz4K);
    --jp-icon-tag: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjgiIGhlaWdodD0iMjgiIHZpZXdCb3g9IjAgMCA0MyAyOCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KCTxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CgkJPHBhdGggZD0iTTI4LjgzMzIgMTIuMzM0TDMyLjk5OTggMTYuNTAwN0wzNy4xNjY1IDEyLjMzNEgyOC44MzMyWiIvPgoJCTxwYXRoIGQ9Ik0xNi4yMDk1IDIxLjYxMDRDMTUuNjg3MyAyMi4xMjk5IDE0Ljg0NDMgMjIuMTI5OSAxNC4zMjQ4IDIxLjYxMDRMNi45ODI5IDE0LjcyNDVDNi41NzI0IDE0LjMzOTQgNi4wODMxMyAxMy42MDk4IDYuMDQ3ODYgMTMuMDQ4MkM1Ljk1MzQ3IDExLjUyODggNi4wMjAwMiA4LjYxOTQ0IDYuMDY2MjEgNy4wNzY5NUM2LjA4MjgxIDYuNTE0NzcgNi41NTU0OCA2LjA0MzQ3IDcuMTE4MDQgNi4wMzA1NUM5LjA4ODYzIDUuOTg0NzMgMTMuMjYzOCA1LjkzNTc5IDEzLjY1MTggNi4zMjQyNUwyMS43MzY5IDEzLjYzOUMyMi4yNTYgMTQuMTU4NSAyMS43ODUxIDE1LjQ3MjQgMjEuMjYyIDE1Ljk5NDZMMTYuMjA5NSAyMS42MTA0Wk05Ljc3NTg1IDguMjY1QzkuMzM1NTEgNy44MjU2NiA4LjYyMzUxIDcuODI1NjYgOC4xODI4IDguMjY1QzcuNzQzNDYgOC43MDU3MSA3Ljc0MzQ2IDkuNDE3MzMgOC4xODI4IDkuODU2NjdDOC42MjM4MiAxMC4yOTY0IDkuMzM1ODIgMTAuMjk2NCA5Ljc3NTg1IDkuODU2NjdDMTAuMjE1NiA5LjQxNzMzIDEwLjIxNTYgOC43MDUzMyA5Ljc3NTg1IDguMjY1WiIvPgoJPC9nPgo8L3N2Zz4K);
    --jp-icon-terminal: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0IiA+CiAgICA8cmVjdCBjbGFzcz0ianAtdGVybWluYWwtaWNvbi1iYWNrZ3JvdW5kLWNvbG9yIGpwLWljb24tc2VsZWN0YWJsZSIgd2lkdGg9IjIwIiBoZWlnaHQ9IjIwIiB0cmFuc2Zvcm09InRyYW5zbGF0ZSgyIDIpIiBmaWxsPSIjMzMzMzMzIi8+CiAgICA8cGF0aCBjbGFzcz0ianAtdGVybWluYWwtaWNvbi1jb2xvciBqcC1pY29uLXNlbGVjdGFibGUtaW52ZXJzZSIgZD0iTTUuMDU2NjQgOC43NjE3MkM1LjA1NjY0IDguNTk3NjYgNS4wMzEyNSA4LjQ1MzEyIDQuOTgwNDcgOC4zMjgxMkM0LjkzMzU5IDguMTk5MjIgNC44NTU0NyA4LjA4MjAzIDQuNzQ2MDkgNy45NzY1NkM0LjY0MDYyIDcuODcxMDkgNC41IDcuNzc1MzkgNC4zMjQyMiA3LjY4OTQ1QzQuMTUyMzQgNy41OTk2MSAzLjk0MzM2IDcuNTExNzIgMy42OTcyNyA3LjQyNTc4QzMuMzAyNzMgNy4yODUxNiAyLjk0MzM2IDcuMTM2NzIgMi42MTkxNCA2Ljk4MDQ3QzIuMjk0OTIgNi44MjQyMiAyLjAxNzU4IDYuNjQyNTggMS43ODcxMSA2LjQzNTU1QzEuNTYwNTUgNi4yMjg1MiAxLjM4NDc3IDUuOTg4MjggMS4yNTk3NyA1LjcxNDg0QzEuMTM0NzcgNS40Mzc1IDEuMDcyMjcgNS4xMDkzOCAxLjA3MjI3IDQuNzMwNDdDMS4wNzIyNyA0LjM5ODQ0IDEuMTI4OTEgNC4wOTU3IDEuMjQyMTkgMy44MjIyN0MxLjM1NTQ3IDMuNTQ0OTIgMS41MTU2MiAzLjMwNDY5IDEuNzIyNjYgMy4xMDE1NkMxLjkyOTY5IDIuODk4NDQgMi4xNzk2OSAyLjczNDM3IDIuNDcyNjYgMi42MDkzOEMyLjc2NTYyIDIuNDg0MzggMy4wOTE4IDIuNDA0MyAzLjQ1MTE3IDIuMzY5MTRWMS4xMDkzOEg0LjM4ODY3VjIuMzgwODZDNC43NDAyMyAyLjQyNzczIDUuMDU2NjQgMi41MjM0NCA1LjMzNzg5IDIuNjY3OTdDNS42MTkxNCAyLjgxMjUgNS44NTc0MiAzLjAwMTk1IDYuMDUyNzMgMy4yMzYzM0M2LjI1MTk1IDMuNDY2OCA2LjQwNDMgMy43NDAyMyA2LjUwOTc3IDQuMDU2NjRDNi42MTkxNCA0LjM2OTE0IDYuNjczODMgNC43MjA3IDYuNjczODMgNS4xMTEzM0g1LjA0NDkyQzUuMDQ0OTIgNC42Mzg2NyA0LjkzNzUgNC4yODEyNSA0LjcyMjY2IDQuMDM5MDZDNC41MDc4MSAzLjc5Mjk3IDQuMjE2OCAzLjY2OTkyIDMuODQ5NjEgMy42Njk5MkMzLjY1MDM5IDMuNjY5OTIgMy40NzY1NiAzLjY5NzI3IDMuMzI4MTIgMy43NTE5NUMzLjE4MzU5IDMuODAyNzMgMy4wNjQ0NSAzLjg3Njk1IDIuOTcwNyAzLjk3NDYxQzIuODc2OTUgNC4wNjgzNiAyLjgwNjY0IDQuMTc5NjkgMi43NTk3NyA0LjMwODU5QzIuNzE2OCA0LjQzNzUgMi42OTUzMSA0LjU3ODEyIDIuNjk1MzEgNC43MzA0N0MyLjY5NTMxIDQuODgyODEgMi43MTY4IDUuMDE5NTMgMi43NTk3NyA1LjE0MDYyQzIuODA2NjQgNS4yNTc4MSAyLjg4MjgxIDUuMzY3MTkgMi45ODgyOCA1LjQ2ODc1QzMuMDk3NjYgNS41NzAzMSAzLjI0MDIzIDUuNjY3OTcgMy40MTYwMiA1Ljc2MTcyQzMuNTkxOCA1Ljg1MTU2IDMuODEwNTUgNS45NDMzNiA0LjA3MjI3IDYuMDM3MTFDNC40NjY4IDYuMTg1NTUgNC44MjQyMiA2LjMzOTg0IDUuMTQ0NTMgNi41QzUuNDY0ODQgNi42NTYyNSA1LjczODI4IDYuODM5ODQgNS45NjQ4NCA3LjA1MDc4QzYuMTk1MzEgNy4yNTc4MSA2LjM3MTA5IDcuNSA2LjQ5MjE5IDcuNzc3MzRDNi42MTcxOSA4LjA1MDc4IDYuNjc5NjkgOC4zNzUgNi42Nzk2OSA4Ljc1QzYuNjc5NjkgOS4wOTM3NSA2LjYyMzA1IDkuNDA0MyA2LjUwOTc3IDkuNjgxNjRDNi4zOTY0OCA5Ljk1NTA4IDYuMjM0MzggMTAuMTkxNCA2LjAyMzQ0IDEwLjM5MDZDNS44MTI1IDEwLjU4OTggNS41NTg1OSAxMC43NSA1LjI2MTcyIDEwLjg3MTFDNC45NjQ4NCAxMC45ODgzIDQuNjMyODEgMTEuMDY0NSA0LjI2NTYyIDExLjA5OTZWMTIuMjQ4SDMuMzMzOThWMTEuMDk5NkMzLjAwMTk1IDExLjA2ODQgMi42Nzk2OSAxMC45OTYxIDIuMzY3MTkgMTAuODgyOEMyLjA1NDY5IDEwLjc2NTYgMS43NzczNCAxMC41OTc3IDEuNTM1MTYgMTAuMzc4OUMxLjI5Njg4IDEwLjE2MDIgMS4xMDU0NyA5Ljg4NDc3IDAuOTYwOTM4IDkuNTUyNzNDMC44MTY0MDYgOS4yMTY4IDAuNzQ0MTQxIDguODE0NDUgMC43NDQxNDEgOC4zNDU3SDIuMzc4OTFDMi4zNzg5MSA4LjYyNjk1IDIuNDE5OTIgOC44NjMyOCAyLjUwMTk1IDkuMDU0NjlDMi41ODM5OCA5LjI0MjE5IDIuNjg5NDUgOS4zOTI1OCAyLjgxODM2IDkuNTA1ODZDMi45NTExNyA5LjYxNTIzIDMuMTAxNTYgOS42OTMzNiAzLjI2OTUzIDkuNzQwMjNDMy40Mzc1IDkuNzg3MTEgMy42MDkzOCA5LjgxMDU1IDMuNzg1MTYgOS44MTA1NUM0LjIwMzEyIDkuODEwNTUgNC41MTk1MyA5LjcxMjg5IDQuNzM0MzggOS41MTc1OEM0Ljk0OTIyIDkuMzIyMjcgNS4wNTY2NCA5LjA3MDMxIDUuMDU2NjQgOC43NjE3MlpNMTMuNDE4IDEyLjI3MTVIOC4wNzQyMlYxMUgxMy40MThWMTIuMjcxNVoiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDMuOTUyNjQgNikiIGZpbGw9IndoaXRlIi8+Cjwvc3ZnPgo=);
    --jp-icon-text-editor: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8cGF0aCBjbGFzcz0ianAtdGV4dC1lZGl0b3ItaWNvbi1jb2xvciBqcC1pY29uLXNlbGVjdGFibGUiIGZpbGw9IiM2MTYxNjEiIGQ9Ik0xNSAxNUgzdjJoMTJ2LTJ6bTAtOEgzdjJoMTJWN3pNMyAxM2gxOHYtMkgzdjJ6bTAgOGgxOHYtMkgzdjJ6TTMgM3YyaDE4VjNIM3oiLz4KPC9zdmc+Cg==);
    --jp-icon-toc: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgdmlld0JveD0iMCAwIDI0IDI0Ij4KICA8ZyBjbGFzcz0ianAtaWNvbjMganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjNjE2MTYxIj4KICAgIDxwYXRoIGQ9Ik03LDVIMjFWN0g3VjVNNywxM1YxMUgyMVYxM0g3TTQsNC41QTEuNSwxLjUgMCAwLDEgNS41LDZBMS41LDEuNSAwIDAsMSA0LDcuNUExLjUsMS41IDAgMCwxIDIuNSw2QTEuNSwxLjUgMCAwLDEgNCw0LjVNNCwxMC41QTEuNSwxLjUgMCAwLDEgNS41LDEyQTEuNSwxLjUgMCAwLDEgNCwxMy41QTEuNSwxLjUgMCAwLDEgMi41LDEyQTEuNSwxLjUgMCAwLDEgNCwxMC41TTcsMTlWMTdIMjFWMTlIN000LDE2LjVBMS41LDEuNSAwIDAsMSA1LjUsMThBMS41LDEuNSAwIDAsMSA0LDE5LjVBMS41LDEuNSAwIDAsMSAyLjUsMThBMS41LDEuNSAwIDAsMSA0LDE2LjVaIiAvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-tree-view: url(data:image/svg+xml;base64,PHN2ZyBoZWlnaHQ9IjI0IiB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICAgIDxnIGNsYXNzPSJqcC1pY29uMyIgZmlsbD0iIzYxNjE2MSI+CiAgICAgICAgPHBhdGggZD0iTTAgMGgyNHYyNEgweiIgZmlsbD0ibm9uZSIvPgogICAgICAgIDxwYXRoIGQ9Ik0yMiAxMVYzaC03djNIOVYzSDJ2OGg3VjhoMnYxMGg0djNoN3YtOGgtN3YzaC0yVjhoMnYzeiIvPgogICAgPC9nPgo8L3N2Zz4K);
    --jp-icon-trusted: url(data:image/svg+xml;base64,PHN2ZyBmaWxsPSJub25lIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDI0IDI1Ij4KICAgIDxwYXRoIGNsYXNzPSJqcC1pY29uMiIgc3Ryb2tlPSIjMzMzMzMzIiBzdHJva2Utd2lkdGg9IjIiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDIgMykiIGQ9Ik0xLjg2MDk0IDExLjQ0MDlDMC44MjY0NDggOC43NzAyNyAwLjg2Mzc3OSA2LjA1NzY0IDEuMjQ5MDcgNC4xOTkzMkMyLjQ4MjA2IDMuOTMzNDcgNC4wODA2OCAzLjQwMzQ3IDUuNjAxMDIgMi44NDQ5QzcuMjM1NDkgMi4yNDQ0IDguODU2NjYgMS41ODE1IDkuOTg3NiAxLjA5NTM5QzExLjA1OTcgMS41ODM0MSAxMi42MDk0IDIuMjQ0NCAxNC4yMTggMi44NDMzOUMxNS43NTAzIDMuNDEzOTQgMTcuMzk5NSAzLjk1MjU4IDE4Ljc1MzkgNC4yMTM4NUMxOS4xMzY0IDYuMDcxNzcgMTkuMTcwOSA4Ljc3NzIyIDE4LjEzOSAxMS40NDA5QzE3LjAzMDMgMTQuMzAzMiAxNC42NjY4IDE3LjE4NDQgOS45OTk5OSAxOC45MzU0QzUuMzMzMiAxNy4xODQ0IDIuOTY5NjggMTQuMzAzMiAxLjg2MDk0IDExLjQ0MDlaIi8+CiAgICA8cGF0aCBjbGFzcz0ianAtaWNvbjIiIGZpbGw9IiMzMzMzMzMiIHN0cm9rZT0iIzMzMzMzMyIgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoOCA5Ljg2NzE5KSIgZD0iTTIuODYwMTUgNC44NjUzNUwwLjcyNjU0OSAyLjk5OTU5TDAgMy42MzA0NUwyLjg2MDE1IDYuMTMxNTdMOCAwLjYzMDg3Mkw3LjI3ODU3IDBMMi44NjAxNSA0Ljg2NTM1WiIvPgo8L3N2Zz4K);
    --jp-icon-undo: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHdpZHRoPSIxNiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTEyLjUgOGMtMi42NSAwLTUuMDUuOTktNi45IDIuNkwyIDd2OWg5bC0zLjYyLTMuNjJjMS4zOS0xLjE2IDMuMTYtMS44OCA1LjEyLTEuODggMy41NCAwIDYuNTUgMi4zMSA3LjYgNS41bDIuMzctLjc4QzIxLjA4IDExLjAzIDE3LjE1IDggMTIuNSA4eiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-user: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIHZpZXdCb3g9IjAgMCAyNCAyNCIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KICA8ZyBjbGFzcz0ianAtaWNvbjMiIGZpbGw9IiM2MTYxNjEiPgogICAgPHBhdGggZD0iTTE2IDdhNCA0IDAgMTEtOCAwIDQgNCAwIDAxOCAwek0xMiAxNGE3IDcgMCAwMC03IDdoMTRhNyA3IDAgMDAtNy03eiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-users: url(data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjQiIGhlaWdodD0iMjQiIHZlcnNpb249IjEuMSIgdmlld0JveD0iMCAwIDM2IDI0IiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciPgogPGcgY2xhc3M9ImpwLWljb24zIiB0cmFuc2Zvcm09Im1hdHJpeCgxLjczMjcgMCAwIDEuNzMyNyAtMy42MjgyIC4wOTk1NzcpIiBmaWxsPSIjNjE2MTYxIj4KICA8cGF0aCB0cmFuc2Zvcm09Im1hdHJpeCgxLjUsMCwwLDEuNSwwLC02KSIgZD0ibTEyLjE4NiA3LjUwOThjLTEuMDUzNSAwLTEuOTc1NyAwLjU2NjUtMi40Nzg1IDEuNDEwMiAwLjc1MDYxIDAuMzEyNzcgMS4zOTc0IDAuODI2NDggMS44NzMgMS40NzI3aDMuNDg2M2MwLTEuNTkyLTEuMjg4OS0yLjg4MjgtMi44ODA5LTIuODgyOHoiLz4KICA8cGF0aCBkPSJtMjAuNDY1IDIuMzg5NWEyLjE4ODUgMi4xODg1IDAgMCAxLTIuMTg4NCAyLjE4ODUgMi4xODg1IDIuMTg4NSAwIDAgMS0yLjE4ODUtMi4xODg1IDIuMTg4NSAyLjE4ODUgMCAwIDEgMi4xODg1LTIuMTg4NSAyLjE4ODUgMi4xODg1IDAgMCAxIDIuMTg4NCAyLjE4ODV6Ii8+CiAgPHBhdGggdHJhbnNmb3JtPSJtYXRyaXgoMS41LDAsMCwxLjUsMCwtNikiIGQ9Im0zLjU4OTggOC40MjE5Yy0xLjExMjYgMC0yLjAxMzcgMC45MDExMS0yLjAxMzcgMi4wMTM3aDIuODE0NWMwLjI2Nzk3LTAuMzczMDkgMC41OTA3LTAuNzA0MzUgMC45NTg5OC0wLjk3ODUyLTAuMzQ0MzMtMC42MTY4OC0xLjAwMzEtMS4wMzUyLTEuNzU5OC0xLjAzNTJ6Ii8+CiAgPHBhdGggZD0ibTYuOTE1NCA0LjYyM2ExLjUyOTQgMS41Mjk0IDAgMCAxLTEuNTI5NCAxLjUyOTQgMS41Mjk0IDEuNTI5NCAwIDAgMS0xLjUyOTQtMS41Mjk0IDEuNTI5NCAxLjUyOTQgMCAwIDEgMS41Mjk0LTEuNTI5NCAxLjUyOTQgMS41Mjk0IDAgMCAxIDEuNTI5NCAxLjUyOTR6Ii8+CiAgPHBhdGggZD0ibTYuMTM1IDEzLjUzNWMwLTMuMjM5MiAyLjYyNTktNS44NjUgNS44NjUtNS44NjUgMy4yMzkyIDAgNS44NjUgMi42MjU5IDUuODY1IDUuODY1eiIvPgogIDxjaXJjbGUgY3g9IjEyIiBjeT0iMy43Njg1IiByPSIyLjk2ODUiLz4KIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-vega: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtaWNvbjEganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjMjEyMTIxIj4KICAgIDxwYXRoIGQ9Ik0xMC42IDUuNGwyLjItMy4ySDIuMnY3LjNsNC02LjZ6Ii8+CiAgICA8cGF0aCBkPSJNMTUuOCAyLjJsLTQuNCA2LjZMNyA2LjNsLTQuOCA4djUuNWgxNy42VjIuMmgtNHptLTcgMTUuNEg1LjV2LTQuNGgzLjN2NC40em00LjQgMEg5LjhWOS44aDMuNHY3Ljh6bTQuNCAwaC0zLjRWNi41aDMuNHYxMS4xeiIvPgogIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-word: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIwIDIwIj4KIDxnIGNsYXNzPSJqcC1pY29uMiIgZmlsbD0iIzQxNDE0MSI+CiAgPHJlY3QgeD0iMiIgeT0iMiIgd2lkdGg9IjE2IiBoZWlnaHQ9IjE2Ii8+CiA8L2c+CiA8ZyBjbGFzcz0ianAtaWNvbi1hY2NlbnQyIiB0cmFuc2Zvcm09InRyYW5zbGF0ZSguNDMgLjA0MDEpIiBmaWxsPSIjZmZmIj4KICA8cGF0aCBkPSJtNC4xNCA4Ljc2cTAuMDY4Mi0xLjg5IDIuNDItMS44OSAxLjE2IDAgMS42OCAwLjQyIDAuNTY3IDAuNDEgMC41NjcgMS4xNnYzLjQ3cTAgMC40NjIgMC41MTQgMC40NjIgMC4xMDMgMCAwLjItMC4wMjMxdjAuNzE0cS0wLjM5OSAwLjEwMy0wLjY1MSAwLjEwMy0wLjQ1MiAwLTAuNjkzLTAuMjItMC4yMzEtMC4yLTAuMjg0LTAuNjYyLTAuOTU2IDAuODcyLTIgMC44NzItMC45MDMgMC0xLjQ3LTAuNDcyLTAuNTI1LTAuNDcyLTAuNTI1LTEuMjYgMC0wLjI2MiAwLjA0NTItMC40NzIgMC4wNTY3LTAuMjIgMC4xMTYtMC4zNzggMC4wNjgyLTAuMTY4IDAuMjMxLTAuMzA0IDAuMTU4LTAuMTQ3IDAuMjYyLTAuMjQyIDAuMTE2LTAuMDkxNCAwLjM2OC0wLjE2OCAwLjI2Mi0wLjA5MTQgMC4zOTktMC4xMjYgMC4xMzYtMC4wNDUyIDAuNDcyLTAuMTAzIDAuMzM2LTAuMDU3OCAwLjUwNC0wLjA3OTggMC4xNTgtMC4wMjMxIDAuNTY3LTAuMDc5OCAwLjU1Ni0wLjA2ODIgMC43NzctMC4yMjEgMC4yMi0wLjE1MiAwLjIyLTAuNDQxdi0wLjI1MnEwLTAuNDMtMC4zNTctMC42NjItMC4zMzYtMC4yMzEtMC45NzYtMC4yMzEtMC42NjIgMC0wLjk5OCAwLjI2Mi0wLjMzNiAwLjI1Mi0wLjM5OSAwLjc5OHptMS44OSAzLjY4cTAuNzg4IDAgMS4yNi0wLjQxIDAuNTA0LTAuNDIgMC41MDQtMC45MDN2LTEuMDVxLTAuMjg0IDAuMTM2LTAuODYxIDAuMjMxLTAuNTY3IDAuMDkxNC0wLjk4NyAwLjE1OC0wLjQyIDAuMDY4Mi0wLjc2NiAwLjMyNi0wLjMzNiAwLjI1Mi0wLjMzNiAwLjcwNHQwLjMwNCAwLjcwNCAwLjg2MSAwLjI1MnoiIHN0cm9rZS13aWR0aD0iMS4wNSIvPgogIDxwYXRoIGQ9Im0xMCA0LjU2aDAuOTQ1djMuMTVxMC42NTEtMC45NzYgMS44OS0wLjk3NiAxLjE2IDAgMS44OSAwLjg0IDAuNjgyIDAuODQgMC42ODIgMi4zMSAwIDEuNDctMC43MDQgMi40Mi0wLjcwNCAwLjg4Mi0xLjg5IDAuODgyLTEuMjYgMC0xLjg5LTEuMDJ2MC43NjZoLTAuODV6bTIuNjIgMy4wNHEtMC43NDYgMC0xLjE2IDAuNjQtMC40NTIgMC42My0wLjQ1MiAxLjY4IDAgMS4wNSAwLjQ1MiAxLjY4dDEuMTYgMC42M3EwLjc3NyAwIDEuMjYtMC42MyAwLjQ5NC0wLjY0IDAuNDk0LTEuNjggMC0xLjA1LTAuNDcyLTEuNjgtMC40NjItMC42NC0xLjI2LTAuNjR6IiBzdHJva2Utd2lkdGg9IjEuMDUiLz4KICA8cGF0aCBkPSJtMi43MyAxNS44IDEzLjYgMC4wMDgxYzAuMDA2OSAwIDAtMi42IDAtMi42IDAtMC4wMDc4LTEuMTUgMC0xLjE1IDAtMC4wMDY5IDAtMC4wMDgzIDEuNS0wLjAwODMgMS41LTJlLTMgLTAuMDAxNC0xMS4zLTAuMDAxNC0xMS4zLTAuMDAxNGwtMC4wMDU5Mi0xLjVjMC0wLjAwNzgtMS4xNyAwLjAwMTMtMS4xNyAwLjAwMTN6IiBzdHJva2Utd2lkdGg9Ii45NzUiLz4KIDwvZz4KPC9zdmc+Cg==);
    --jp-icon-yaml: url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgdmlld0JveD0iMCAwIDIyIDIyIj4KICA8ZyBjbGFzcz0ianAtaWNvbi1jb250cmFzdDIganAtaWNvbi1zZWxlY3RhYmxlIiBmaWxsPSIjRDgxQjYwIj4KICAgIDxwYXRoIGQ9Ik03LjIgMTguNnYtNS40TDMgNS42aDMuM2wxLjQgMy4xYy4zLjkuNiAxLjYgMSAyLjUuMy0uOC42LTEuNiAxLTIuNWwxLjQtMy4xaDMuNGwtNC40IDcuNnY1LjVsLTIuOS0uMXoiLz4KICAgIDxjaXJjbGUgY2xhc3M9InN0MCIgY3g9IjE3LjYiIGN5PSIxNi41IiByPSIyLjEiLz4KICAgIDxjaXJjbGUgY2xhc3M9InN0MCIgY3g9IjE3LjYiIGN5PSIxMSIgcj0iMi4xIi8+CiAgPC9nPgo8L3N2Zz4K);
    }

    /* Icon CSS class declarations */

    .jp-AddAboveIcon {
    background-image: var(--jp-icon-add-above);
    }

    .jp-AddBelowIcon {
    background-image: var(--jp-icon-add-below);
    }

    .jp-AddIcon {
    background-image: var(--jp-icon-add);
    }

    .jp-BellIcon {
    background-image: var(--jp-icon-bell);
    }

    .jp-BugDotIcon {
    background-image: var(--jp-icon-bug-dot);
    }

    .jp-BugIcon {
    background-image: var(--jp-icon-bug);
    }

    .jp-BuildIcon {
    background-image: var(--jp-icon-build);
    }

    .jp-CaretDownEmptyIcon {
    background-image: var(--jp-icon-caret-down-empty);
    }

    .jp-CaretDownEmptyThinIcon {
    background-image: var(--jp-icon-caret-down-empty-thin);
    }

    .jp-CaretDownIcon {
    background-image: var(--jp-icon-caret-down);
    }

    .jp-CaretLeftIcon {
    background-image: var(--jp-icon-caret-left);
    }

    .jp-CaretRightIcon {
    background-image: var(--jp-icon-caret-right);
    }

    .jp-CaretUpEmptyThinIcon {
    background-image: var(--jp-icon-caret-up-empty-thin);
    }

    .jp-CaretUpIcon {
    background-image: var(--jp-icon-caret-up);
    }

    .jp-CaseSensitiveIcon {
    background-image: var(--jp-icon-case-sensitive);
    }

    .jp-CheckIcon {
    background-image: var(--jp-icon-check);
    }

    .jp-CircleEmptyIcon {
    background-image: var(--jp-icon-circle-empty);
    }

    .jp-CircleIcon {
    background-image: var(--jp-icon-circle);
    }

    .jp-ClearIcon {
    background-image: var(--jp-icon-clear);
    }

    .jp-CloseIcon {
    background-image: var(--jp-icon-close);
    }

    .jp-CodeCheckIcon {
    background-image: var(--jp-icon-code-check);
    }

    .jp-CodeIcon {
    background-image: var(--jp-icon-code);
    }

    .jp-CollapseAllIcon {
    background-image: var(--jp-icon-collapse-all);
    }

    .jp-ConsoleIcon {
    background-image: var(--jp-icon-console);
    }

    .jp-CopyIcon {
    background-image: var(--jp-icon-copy);
    }

    .jp-CopyrightIcon {
    background-image: var(--jp-icon-copyright);
    }

    .jp-CutIcon {
    background-image: var(--jp-icon-cut);
    }

    .jp-DeleteIcon {
    background-image: var(--jp-icon-delete);
    }

    .jp-DownloadIcon {
    background-image: var(--jp-icon-download);
    }

    .jp-DuplicateIcon {
    background-image: var(--jp-icon-duplicate);
    }

    .jp-EditIcon {
    background-image: var(--jp-icon-edit);
    }

    .jp-EllipsesIcon {
    background-image: var(--jp-icon-ellipses);
    }

    .jp-ErrorIcon {
    background-image: var(--jp-icon-error);
    }

    .jp-ExpandAllIcon {
    background-image: var(--jp-icon-expand-all);
    }

    .jp-ExtensionIcon {
    background-image: var(--jp-icon-extension);
    }

    .jp-FastForwardIcon {
    background-image: var(--jp-icon-fast-forward);
    }

    .jp-FileIcon {
    background-image: var(--jp-icon-file);
    }

    .jp-FileUploadIcon {
    background-image: var(--jp-icon-file-upload);
    }

    .jp-FilterDotIcon {
    background-image: var(--jp-icon-filter-dot);
    }

    .jp-FilterIcon {
    background-image: var(--jp-icon-filter);
    }

    .jp-FilterListIcon {
    background-image: var(--jp-icon-filter-list);
    }

    .jp-FolderFavoriteIcon {
    background-image: var(--jp-icon-folder-favorite);
    }

    .jp-FolderIcon {
    background-image: var(--jp-icon-folder);
    }

    .jp-HomeIcon {
    background-image: var(--jp-icon-home);
    }

    .jp-Html5Icon {
    background-image: var(--jp-icon-html5);
    }

    .jp-ImageIcon {
    background-image: var(--jp-icon-image);
    }

    .jp-InfoIcon {
    background-image: var(--jp-icon-info);
    }

    .jp-InspectorIcon {
    background-image: var(--jp-icon-inspector);
    }

    .jp-JsonIcon {
    background-image: var(--jp-icon-json);
    }

    .jp-JuliaIcon {
    background-image: var(--jp-icon-julia);
    }

    .jp-JupyterFaviconIcon {
    background-image: var(--jp-icon-jupyter-favicon);
    }

    .jp-JupyterIcon {
    background-image: var(--jp-icon-jupyter);
    }

    .jp-JupyterlabWordmarkIcon {
    background-image: var(--jp-icon-jupyterlab-wordmark);
    }

    .jp-KernelIcon {
    background-image: var(--jp-icon-kernel);
    }

    .jp-KeyboardIcon {
    background-image: var(--jp-icon-keyboard);
    }

    .jp-LaunchIcon {
    background-image: var(--jp-icon-launch);
    }

    .jp-LauncherIcon {
    background-image: var(--jp-icon-launcher);
    }

    .jp-LineFormIcon {
    background-image: var(--jp-icon-line-form);
    }

    .jp-LinkIcon {
    background-image: var(--jp-icon-link);
    }

    .jp-ListIcon {
    background-image: var(--jp-icon-list);
    }

    .jp-MarkdownIcon {
    background-image: var(--jp-icon-markdown);
    }

    .jp-MoveDownIcon {
    background-image: var(--jp-icon-move-down);
    }

    .jp-MoveUpIcon {
    background-image: var(--jp-icon-move-up);
    }

    .jp-NewFolderIcon {
    background-image: var(--jp-icon-new-folder);
    }

    .jp-NotTrustedIcon {
    background-image: var(--jp-icon-not-trusted);
    }

    .jp-NotebookIcon {
    background-image: var(--jp-icon-notebook);
    }

    .jp-NumberingIcon {
    background-image: var(--jp-icon-numbering);
    }

    .jp-OfflineBoltIcon {
    background-image: var(--jp-icon-offline-bolt);
    }

    .jp-PaletteIcon {
    background-image: var(--jp-icon-palette);
    }

    .jp-PasteIcon {
    background-image: var(--jp-icon-paste);
    }

    .jp-PdfIcon {
    background-image: var(--jp-icon-pdf);
    }

    .jp-PythonIcon {
    background-image: var(--jp-icon-python);
    }

    .jp-RKernelIcon {
    background-image: var(--jp-icon-r-kernel);
    }

    .jp-ReactIcon {
    background-image: var(--jp-icon-react);
    }

    .jp-RedoIcon {
    background-image: var(--jp-icon-redo);
    }

    .jp-RefreshIcon {
    background-image: var(--jp-icon-refresh);
    }

    .jp-RegexIcon {
    background-image: var(--jp-icon-regex);
    }

    .jp-RunIcon {
    background-image: var(--jp-icon-run);
    }

    .jp-RunningIcon {
    background-image: var(--jp-icon-running);
    }

    .jp-SaveIcon {
    background-image: var(--jp-icon-save);
    }

    .jp-SearchIcon {
    background-image: var(--jp-icon-search);
    }

    .jp-SettingsIcon {
    background-image: var(--jp-icon-settings);
    }

    .jp-ShareIcon {
    background-image: var(--jp-icon-share);
    }

    .jp-SpreadsheetIcon {
    background-image: var(--jp-icon-spreadsheet);
    }

    .jp-StopIcon {
    background-image: var(--jp-icon-stop);
    }

    .jp-TabIcon {
    background-image: var(--jp-icon-tab);
    }

    .jp-TableRowsIcon {
    background-image: var(--jp-icon-table-rows);
    }

    .jp-TagIcon {
    background-image: var(--jp-icon-tag);
    }

    .jp-TerminalIcon {
    background-image: var(--jp-icon-terminal);
    }

    .jp-TextEditorIcon {
    background-image: var(--jp-icon-text-editor);
    }

    .jp-TocIcon {
    background-image: var(--jp-icon-toc);
    }

    .jp-TreeViewIcon {
    background-image: var(--jp-icon-tree-view);
    }

    .jp-TrustedIcon {
    background-image: var(--jp-icon-trusted);
    }

    .jp-UndoIcon {
    background-image: var(--jp-icon-undo);
    }

    .jp-UserIcon {
    background-image: var(--jp-icon-user);
    }

    .jp-UsersIcon {
    background-image: var(--jp-icon-users);
    }

    .jp-VegaIcon {
    background-image: var(--jp-icon-vega);
    }

    .jp-WordIcon {
    background-image: var(--jp-icon-word);
    }

    .jp-YamlIcon {
    background-image: var(--jp-icon-yaml);
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    /**
    * (DEPRECATED) Support for consuming icons as CSS background images
    */

    .jp-Icon,
    .jp-MaterialIcon {
    background-position: center;
    background-repeat: no-repeat;
    background-size: 16px;
    min-width: 16px;
    min-height: 16px;
    }

    .jp-Icon-cover {
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
    }

    /**
    * (DEPRECATED) Support for specific CSS icon sizes
    */

    .jp-Icon-16 {
    background-size: 16px;
    min-width: 16px;
    min-height: 16px;
    }

    .jp-Icon-18 {
    background-size: 18px;
    min-width: 18px;
    min-height: 18px;
    }

    .jp-Icon-20 {
    background-size: 20px;
    min-width: 20px;
    min-height: 20px;
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    .lm-TabBar .lm-TabBar-addButton {
    align-items: center;
    display: flex;
    padding: 4px;
    padding-bottom: 5px;
    margin-right: 1px;
    background-color: var(--jp-layout-color2);
    }

    .lm-TabBar .lm-TabBar-addButton:hover {
    background-color: var(--jp-layout-color1);
    }

    .lm-DockPanel-tabBar .lm-TabBar-tab {
    width: var(--jp-private-horizontal-tab-width);
    }

    .lm-DockPanel-tabBar .lm-TabBar-content {
    flex: unset;
    }

    .lm-DockPanel-tabBar[data-orientation='horizontal'] {
    flex: 1 1 auto;
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    /**
    * Support for icons as inline SVG HTMLElements
    */

    /* recolor the primary elements of an icon */
    .jp-icon0[fill] {
    fill: var(--jp-inverse-layout-color0);
    }

    .jp-icon1[fill] {
    fill: var(--jp-inverse-layout-color1);
    }

    .jp-icon2[fill] {
    fill: var(--jp-inverse-layout-color2);
    }

    .jp-icon3[fill] {
    fill: var(--jp-inverse-layout-color3);
    }

    .jp-icon4[fill] {
    fill: var(--jp-inverse-layout-color4);
    }

    .jp-icon0[stroke] {
    stroke: var(--jp-inverse-layout-color0);
    }

    .jp-icon1[stroke] {
    stroke: var(--jp-inverse-layout-color1);
    }

    .jp-icon2[stroke] {
    stroke: var(--jp-inverse-layout-color2);
    }

    .jp-icon3[stroke] {
    stroke: var(--jp-inverse-layout-color3);
    }

    .jp-icon4[stroke] {
    stroke: var(--jp-inverse-layout-color4);
    }

    /* recolor the accent elements of an icon */
    .jp-icon-accent0[fill] {
    fill: var(--jp-layout-color0);
    }

    .jp-icon-accent1[fill] {
    fill: var(--jp-layout-color1);
    }

    .jp-icon-accent2[fill] {
    fill: var(--jp-layout-color2);
    }

    .jp-icon-accent3[fill] {
    fill: var(--jp-layout-color3);
    }

    .jp-icon-accent4[fill] {
    fill: var(--jp-layout-color4);
    }

    .jp-icon-accent0[stroke] {
    stroke: var(--jp-layout-color0);
    }

    .jp-icon-accent1[stroke] {
    stroke: var(--jp-layout-color1);
    }

    .jp-icon-accent2[stroke] {
    stroke: var(--jp-layout-color2);
    }

    .jp-icon-accent3[stroke] {
    stroke: var(--jp-layout-color3);
    }

    .jp-icon-accent4[stroke] {
    stroke: var(--jp-layout-color4);
    }

    /* set the color of an icon to transparent */
    .jp-icon-none[fill] {
    fill: none;
    }

    .jp-icon-none[stroke] {
    stroke: none;
    }

    /* brand icon colors. Same for light and dark */
    .jp-icon-brand0[fill] {
    fill: var(--jp-brand-color0);
    }

    .jp-icon-brand1[fill] {
    fill: var(--jp-brand-color1);
    }

    .jp-icon-brand2[fill] {
    fill: var(--jp-brand-color2);
    }

    .jp-icon-brand3[fill] {
    fill: var(--jp-brand-color3);
    }

    .jp-icon-brand4[fill] {
    fill: var(--jp-brand-color4);
    }

    .jp-icon-brand0[stroke] {
    stroke: var(--jp-brand-color0);
    }

    .jp-icon-brand1[stroke] {
    stroke: var(--jp-brand-color1);
    }

    .jp-icon-brand2[stroke] {
    stroke: var(--jp-brand-color2);
    }

    .jp-icon-brand3[stroke] {
    stroke: var(--jp-brand-color3);
    }

    .jp-icon-brand4[stroke] {
    stroke: var(--jp-brand-color4);
    }

    /* warn icon colors. Same for light and dark */
    .jp-icon-warn0[fill] {
    fill: var(--jp-warn-color0);
    }

    .jp-icon-warn1[fill] {
    fill: var(--jp-warn-color1);
    }

    .jp-icon-warn2[fill] {
    fill: var(--jp-warn-color2);
    }

    .jp-icon-warn3[fill] {
    fill: var(--jp-warn-color3);
    }

    .jp-icon-warn0[stroke] {
    stroke: var(--jp-warn-color0);
    }

    .jp-icon-warn1[stroke] {
    stroke: var(--jp-warn-color1);
    }

    .jp-icon-warn2[stroke] {
    stroke: var(--jp-warn-color2);
    }

    .jp-icon-warn3[stroke] {
    stroke: var(--jp-warn-color3);
    }

    /* icon colors that contrast well with each other and most backgrounds */
    .jp-icon-contrast0[fill] {
    fill: var(--jp-icon-contrast-color0);
    }

    .jp-icon-contrast1[fill] {
    fill: var(--jp-icon-contrast-color1);
    }

    .jp-icon-contrast2[fill] {
    fill: var(--jp-icon-contrast-color2);
    }

    .jp-icon-contrast3[fill] {
    fill: var(--jp-icon-contrast-color3);
    }

    .jp-icon-contrast0[stroke] {
    stroke: var(--jp-icon-contrast-color0);
    }

    .jp-icon-contrast1[stroke] {
    stroke: var(--jp-icon-contrast-color1);
    }

    .jp-icon-contrast2[stroke] {
    stroke: var(--jp-icon-contrast-color2);
    }

    .jp-icon-contrast3[stroke] {
    stroke: var(--jp-icon-contrast-color3);
    }

    .jp-icon-dot[fill] {
    fill: var(--jp-warn-color0);
    }

    .jp-jupyter-icon-color[fill] {
    fill: var(--jp-jupyter-icon-color, var(--jp-warn-color0));
    }

    .jp-notebook-icon-color[fill] {
    fill: var(--jp-notebook-icon-color, var(--jp-warn-color0));
    }

    .jp-json-icon-color[fill] {
    fill: var(--jp-json-icon-color, var(--jp-warn-color1));
    }

    .jp-console-icon-color[fill] {
    fill: var(--jp-console-icon-color, white);
    }

    .jp-console-icon-background-color[fill] {
    fill: var(--jp-console-icon-background-color, var(--jp-brand-color1));
    }

    .jp-terminal-icon-color[fill] {
    fill: var(--jp-terminal-icon-color, var(--jp-layout-color2));
    }

    .jp-terminal-icon-background-color[fill] {
    fill: var(
        --jp-terminal-icon-background-color,
        var(--jp-inverse-layout-color2)
    );
    }

    .jp-text-editor-icon-color[fill] {
    fill: var(--jp-text-editor-icon-color, var(--jp-inverse-layout-color3));
    }

    .jp-inspector-icon-color[fill] {
    fill: var(--jp-inspector-icon-color, var(--jp-inverse-layout-color3));
    }

    /* CSS for icons in selected filebrowser listing items */
    .jp-DirListing-item.jp-mod-selected .jp-icon-selectable[fill] {
    fill: #fff;
    }

    .jp-DirListing-item.jp-mod-selected .jp-icon-selectable-inverse[fill] {
    fill: var(--jp-brand-color1);
    }

    /* stylelint-disable selector-max-class, selector-max-compound-selectors */

    /**
    * TODO: come up with non css-hack solution for showing the busy icon on top
    *  of the close icon
    * CSS for complex behavior of close icon of tabs in the main area tabbar
    */
    .lm-DockPanel-tabBar
    .lm-TabBar-tab.lm-mod-closable.jp-mod-dirty
    > .lm-TabBar-tabCloseIcon
    > :not(:hover)
    > .jp-icon3[fill] {
    fill: none;
    }

    .lm-DockPanel-tabBar
    .lm-TabBar-tab.lm-mod-closable.jp-mod-dirty
    > .lm-TabBar-tabCloseIcon
    > :not(:hover)
    > .jp-icon-busy[fill] {
    fill: var(--jp-inverse-layout-color3);
    }

    /* stylelint-enable selector-max-class, selector-max-compound-selectors */

    /* CSS for icons in status bar */
    #jp-main-statusbar .jp-mod-selected .jp-icon-selectable[fill] {
    fill: #fff;
    }

    #jp-main-statusbar .jp-mod-selected .jp-icon-selectable-inverse[fill] {
    fill: var(--jp-brand-color1);
    }

    /* special handling for splash icon CSS. While the theme CSS reloads during
    splash, the splash icon can loose theming. To prevent that, we set a
    default for its color variable */
    :root {
    --jp-warn-color0: var(--md-orange-700);
    }

    /* not sure what to do with this one, used in filebrowser listing */
    .jp-DragIcon {
    margin-right: 4px;
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    /**
    * Support for alt colors for icons as inline SVG HTMLElements
    */

    /* alt recolor the primary elements of an icon */
    .jp-icon-alt .jp-icon0[fill] {
    fill: var(--jp-layout-color0);
    }

    .jp-icon-alt .jp-icon1[fill] {
    fill: var(--jp-layout-color1);
    }

    .jp-icon-alt .jp-icon2[fill] {
    fill: var(--jp-layout-color2);
    }

    .jp-icon-alt .jp-icon3[fill] {
    fill: var(--jp-layout-color3);
    }

    .jp-icon-alt .jp-icon4[fill] {
    fill: var(--jp-layout-color4);
    }

    .jp-icon-alt .jp-icon0[stroke] {
    stroke: var(--jp-layout-color0);
    }

    .jp-icon-alt .jp-icon1[stroke] {
    stroke: var(--jp-layout-color1);
    }

    .jp-icon-alt .jp-icon2[stroke] {
    stroke: var(--jp-layout-color2);
    }

    .jp-icon-alt .jp-icon3[stroke] {
    stroke: var(--jp-layout-color3);
    }

    .jp-icon-alt .jp-icon4[stroke] {
    stroke: var(--jp-layout-color4);
    }

    /* alt recolor the accent elements of an icon */
    .jp-icon-alt .jp-icon-accent0[fill] {
    fill: var(--jp-inverse-layout-color0);
    }

    .jp-icon-alt .jp-icon-accent1[fill] {
    fill: var(--jp-inverse-layout-color1);
    }

    .jp-icon-alt .jp-icon-accent2[fill] {
    fill: var(--jp-inverse-layout-color2);
    }

    .jp-icon-alt .jp-icon-accent3[fill] {
    fill: var(--jp-inverse-layout-color3);
    }

    .jp-icon-alt .jp-icon-accent4[fill] {
    fill: var(--jp-inverse-layout-color4);
    }

    .jp-icon-alt .jp-icon-accent0[stroke] {
    stroke: var(--jp-inverse-layout-color0);
    }

    .jp-icon-alt .jp-icon-accent1[stroke] {
    stroke: var(--jp-inverse-layout-color1);
    }

    .jp-icon-alt .jp-icon-accent2[stroke] {
    stroke: var(--jp-inverse-layout-color2);
    }

    .jp-icon-alt .jp-icon-accent3[stroke] {
    stroke: var(--jp-inverse-layout-color3);
    }

    .jp-icon-alt .jp-icon-accent4[stroke] {
    stroke: var(--jp-inverse-layout-color4);
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    .jp-icon-hoverShow:not(:hover) .jp-icon-hoverShow-content {
    display: none !important;
    }

    /**
    * Support for hover colors for icons as inline SVG HTMLElements
    */

    /**
    * regular colors
    */

    /* recolor the primary elements of an icon */
    .jp-icon-hover :hover .jp-icon0-hover[fill] {
    fill: var(--jp-inverse-layout-color0);
    }

    .jp-icon-hover :hover .jp-icon1-hover[fill] {
    fill: var(--jp-inverse-layout-color1);
    }

    .jp-icon-hover :hover .jp-icon2-hover[fill] {
    fill: var(--jp-inverse-layout-color2);
    }

    .jp-icon-hover :hover .jp-icon3-hover[fill] {
    fill: var(--jp-inverse-layout-color3);
    }

    .jp-icon-hover :hover .jp-icon4-hover[fill] {
    fill: var(--jp-inverse-layout-color4);
    }

    .jp-icon-hover :hover .jp-icon0-hover[stroke] {
    stroke: var(--jp-inverse-layout-color0);
    }

    .jp-icon-hover :hover .jp-icon1-hover[stroke] {
    stroke: var(--jp-inverse-layout-color1);
    }

    .jp-icon-hover :hover .jp-icon2-hover[stroke] {
    stroke: var(--jp-inverse-layout-color2);
    }

    .jp-icon-hover :hover .jp-icon3-hover[stroke] {
    stroke: var(--jp-inverse-layout-color3);
    }

    .jp-icon-hover :hover .jp-icon4-hover[stroke] {
    stroke: var(--jp-inverse-layout-color4);
    }

    /* recolor the accent elements of an icon */
    .jp-icon-hover :hover .jp-icon-accent0-hover[fill] {
    fill: var(--jp-layout-color0);
    }

    .jp-icon-hover :hover .jp-icon-accent1-hover[fill] {
    fill: var(--jp-layout-color1);
    }

    .jp-icon-hover :hover .jp-icon-accent2-hover[fill] {
    fill: var(--jp-layout-color2);
    }

    .jp-icon-hover :hover .jp-icon-accent3-hover[fill] {
    fill: var(--jp-layout-color3);
    }

    .jp-icon-hover :hover .jp-icon-accent4-hover[fill] {
    fill: var(--jp-layout-color4);
    }

    .jp-icon-hover :hover .jp-icon-accent0-hover[stroke] {
    stroke: var(--jp-layout-color0);
    }

    .jp-icon-hover :hover .jp-icon-accent1-hover[stroke] {
    stroke: var(--jp-layout-color1);
    }

    .jp-icon-hover :hover .jp-icon-accent2-hover[stroke] {
    stroke: var(--jp-layout-color2);
    }

    .jp-icon-hover :hover .jp-icon-accent3-hover[stroke] {
    stroke: var(--jp-layout-color3);
    }

    .jp-icon-hover :hover .jp-icon-accent4-hover[stroke] {
    stroke: var(--jp-layout-color4);
    }

    /* set the color of an icon to transparent */
    .jp-icon-hover :hover .jp-icon-none-hover[fill] {
    fill: none;
    }

    .jp-icon-hover :hover .jp-icon-none-hover[stroke] {
    stroke: none;
    }

    /**
    * inverse colors
    */

    /* inverse recolor the primary elements of an icon */
    .jp-icon-hover.jp-icon-alt :hover .jp-icon0-hover[fill] {
    fill: var(--jp-layout-color0);
    }

    .jp-icon-hover.jp-icon-alt :hover .jp-icon1-hover[fill] {
    fill: var(--jp-layout-color1);
    }

    .jp-icon-hover.jp-icon-alt :hover .jp-icon2-hover[fill] {
    fill: var(--jp-layout-color2);
    }

    .jp-icon-hover.jp-icon-alt :hover .jp-icon3-hover[fill] {
    fill: var(--jp-layout-color3);
    }

    .jp-icon-hover.jp-icon-alt :hover .jp-icon4-hover[fill] {
    fill: var(--jp-layout-color4);
    }

    .jp-icon-hover.jp-icon-alt :hover .jp-icon0-hover[stroke] {
    stroke: var(--jp-layout-color0);
    }

    .jp-icon-hover.jp-icon-alt :hover .jp-icon1-hover[stroke] {
    stroke: var(--jp-layout-color1);
    }

    .jp-icon-hover.jp-icon-alt :hover .jp-icon2-hover[stroke] {
    stroke: var(--jp-layout-color2);
    }

    .jp-icon-hover.jp-icon-alt :hover .jp-icon3-hover[stroke] {
    stroke: var(--jp-layout-color3);
    }

    .jp-icon-hover.jp-icon-alt :hover .jp-icon4-hover[stroke] {
    stroke: var(--jp-layout-color4);
    }

    /* inverse recolor the accent elements of an icon */
    .jp-icon-hover.jp-icon-alt :hover .jp-icon-accent0-hover[fill] {
    fill: var(--jp-inverse-layout-color0);
    }

    .jp-icon-hover.jp-icon-alt :hover .jp-icon-accent1-hover[fill] {
    fill: var(--jp-inverse-layout-color1);
    }

    .jp-icon-hover.jp-icon-alt :hover .jp-icon-accent2-hover[fill] {
    fill: var(--jp-inverse-layout-color2);
    }

    .jp-icon-hover.jp-icon-alt :hover .jp-icon-accent3-hover[fill] {
    fill: var(--jp-inverse-layout-color3);
    }

    .jp-icon-hover.jp-icon-alt :hover .jp-icon-accent4-hover[fill] {
    fill: var(--jp-inverse-layout-color4);
    }

    .jp-icon-hover.jp-icon-alt :hover .jp-icon-accent0-hover[stroke] {
    stroke: var(--jp-inverse-layout-color0);
    }

    .jp-icon-hover.jp-icon-alt :hover .jp-icon-accent1-hover[stroke] {
    stroke: var(--jp-inverse-layout-color1);
    }

    .jp-icon-hover.jp-icon-alt :hover .jp-icon-accent2-hover[stroke] {
    stroke: var(--jp-inverse-layout-color2);
    }

    .jp-icon-hover.jp-icon-alt :hover .jp-icon-accent3-hover[stroke] {
    stroke: var(--jp-inverse-layout-color3);
    }

    .jp-icon-hover.jp-icon-alt :hover .jp-icon-accent4-hover[stroke] {
    stroke: var(--jp-inverse-layout-color4);
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    .jp-IFrame {
    width: 100%;
    height: 100%;
    }

    .jp-IFrame > iframe {
    border: none;
    }

    /*
    When drag events occur, `lm-mod-override-cursor` is added to the body.
    Because iframes steal all cursor events, the following two rules are necessary
    to suppress pointer events while resize drags are occurring. There may be a
    better solution to this problem.
    */
    body.lm-mod-override-cursor .jp-IFrame {
    position: relative;
    }

    body.lm-mod-override-cursor .jp-IFrame::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: transparent;
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) 2014-2016, Jupyter Development Team.
    |
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    .jp-HoverBox {
    position: fixed;
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    .jp-FormGroup-content fieldset {
    border: none;
    padding: 0;
    min-width: 0;
    width: 100%;
    }

    /* stylelint-disable selector-max-type */

    .jp-FormGroup-content fieldset .jp-inputFieldWrapper input,
    .jp-FormGroup-content fieldset .jp-inputFieldWrapper select,
    .jp-FormGroup-content fieldset .jp-inputFieldWrapper textarea {
    font-size: var(--jp-content-font-size2);
    border-color: var(--jp-input-border-color);
    border-style: solid;
    border-radius: var(--jp-border-radius);
    border-width: 1px;
    padding: 6px 8px;
    background: none;
    color: var(--jp-ui-font-color0);
    height: inherit;
    }

    .jp-FormGroup-content fieldset input[type='checkbox'] {
    position: relative;
    top: 2px;
    margin-left: 0;
    }

    .jp-FormGroup-content button.jp-mod-styled {
    cursor: pointer;
    }

    .jp-FormGroup-content .checkbox label {
    cursor: pointer;
    font-size: var(--jp-content-font-size1);
    }

    .jp-FormGroup-content .jp-root > fieldset > legend {
    display: none;
    }

    .jp-FormGroup-content .jp-root > fieldset > p {
    display: none;
    }

    /** copy of `input.jp-mod-styled:focus` style */
    .jp-FormGroup-content fieldset input:focus,
    .jp-FormGroup-content fieldset select:focus {
    -moz-outline-radius: unset;
    outline: var(--jp-border-width) solid var(--md-blue-500);
    outline-offset: -1px;
    box-shadow: inset 0 0 4px var(--md-blue-300);
    }

    .jp-FormGroup-content fieldset input:hover:not(:focus),
    .jp-FormGroup-content fieldset select:hover:not(:focus) {
    background-color: var(--jp-border-color2);
    }

    /* stylelint-enable selector-max-type */

    .jp-FormGroup-content .checkbox .field-description {
    /* Disable default description field for checkbox:
    because other widgets do not have description fields,
    we add descriptions to each widget on the field level.
    */
    display: none;
    }

    .jp-FormGroup-content #root__description {
    display: none;
    }

    .jp-FormGroup-content .jp-modifiedIndicator {
    width: 5px;
    background-color: var(--jp-brand-color2);
    margin-top: 0;
    margin-left: calc(var(--jp-private-settingeditor-modifier-indent) * -1);
    flex-shrink: 0;
    }

    .jp-FormGroup-content .jp-modifiedIndicator.jp-errorIndicator {
    background-color: var(--jp-error-color0);
    margin-right: 0.5em;
    }

    /* RJSF ARRAY style */

    .jp-arrayFieldWrapper legend {
    font-size: var(--jp-content-font-size2);
    color: var(--jp-ui-font-color0);
    flex-basis: 100%;
    padding: 4px 0;
    font-weight: var(--jp-content-heading-font-weight);
    border-bottom: 1px solid var(--jp-border-color2);
    }

    .jp-arrayFieldWrapper .field-description {
    padding: 4px 0;
    white-space: pre-wrap;
    }

    .jp-arrayFieldWrapper .array-item {
    width: 100%;
    border: 1px solid var(--jp-border-color2);
    border-radius: 4px;
    margin: 4px;
    }

    .jp-ArrayOperations {
    display: flex;
    margin-left: 8px;
    }

    .jp-ArrayOperationsButton {
    margin: 2px;
    }

    .jp-ArrayOperationsButton .jp-icon3[fill] {
    fill: var(--jp-ui-font-color0);
    }

    button.jp-ArrayOperationsButton.jp-mod-styled:disabled {
    cursor: not-allowed;
    opacity: 0.5;
    }

    /* RJSF form validation error */

    .jp-FormGroup-content .validationErrors {
    color: var(--jp-error-color0);
    }

    /* Hide panel level error as duplicated the field level error */
    .jp-FormGroup-content .panel.errors {
    display: none;
    }

    /* RJSF normal content (settings-editor) */

    .jp-FormGroup-contentNormal {
    display: flex;
    align-items: center;
    flex-wrap: wrap;
    }

    .jp-FormGroup-contentNormal .jp-FormGroup-contentItem {
    margin-left: 7px;
    color: var(--jp-ui-font-color0);
    }

    .jp-FormGroup-contentNormal .jp-FormGroup-description {
    flex-basis: 100%;
    padding: 4px 7px;
    }

    .jp-FormGroup-contentNormal .jp-FormGroup-default {
    flex-basis: 100%;
    padding: 4px 7px;
    }

    .jp-FormGroup-contentNormal .jp-FormGroup-fieldLabel {
    font-size: var(--jp-content-font-size1);
    font-weight: normal;
    min-width: 120px;
    }

    .jp-FormGroup-contentNormal fieldset:not(:first-child) {
    margin-left: 7px;
    }

    .jp-FormGroup-contentNormal .field-array-of-string .array-item {
    /* Display `jp-ArrayOperations` buttons side-by-side with content except
        for small screens where flex-wrap will place them one below the other.
    */
    display: flex;
    align-items: center;
    flex-wrap: wrap;
    }

    .jp-FormGroup-contentNormal .jp-objectFieldWrapper .form-group {
    padding: 2px 8px 2px var(--jp-private-settingeditor-modifier-indent);
    margin-top: 2px;
    }

    /* RJSF compact content (metadata-form) */

    .jp-FormGroup-content.jp-FormGroup-contentCompact {
    width: 100%;
    }

    .jp-FormGroup-contentCompact .form-group {
    display: flex;
    padding: 0.5em 0.2em 0.5em 0;
    }

    .jp-FormGroup-contentCompact
    .jp-FormGroup-compactTitle
    .jp-FormGroup-description {
    font-size: var(--jp-ui-font-size1);
    color: var(--jp-ui-font-color2);
    }

    .jp-FormGroup-contentCompact .jp-FormGroup-fieldLabel {
    padding-bottom: 0.3em;
    }

    .jp-FormGroup-contentCompact .jp-inputFieldWrapper .form-control {
    width: 100%;
    box-sizing: border-box;
    }

    .jp-FormGroup-contentCompact .jp-arrayFieldWrapper .jp-FormGroup-compactTitle {
    padding-bottom: 7px;
    }

    .jp-FormGroup-contentCompact
    .jp-objectFieldWrapper
    .jp-objectFieldWrapper
    .form-group {
    padding: 2px 8px 2px var(--jp-private-settingeditor-modifier-indent);
    margin-top: 2px;
    }

    .jp-FormGroup-contentCompact ul.error-detail {
    margin-block-start: 0.5em;
    margin-block-end: 0.5em;
    padding-inline-start: 1em;
    }

    /*
    * Copyright (c) Jupyter Development Team.
    * Distributed under the terms of the Modified BSD License.
    */

    .jp-SidePanel {
    display: flex;
    flex-direction: column;
    min-width: var(--jp-sidebar-min-width);
    overflow-y: auto;
    color: var(--jp-ui-font-color1);
    background: var(--jp-layout-color1);
    font-size: var(--jp-ui-font-size1);
    }

    .jp-SidePanel-header {
    flex: 0 0 auto;
    display: flex;
    border-bottom: var(--jp-border-width) solid var(--jp-border-color2);
    font-size: var(--jp-ui-font-size0);
    font-weight: 600;
    letter-spacing: 1px;
    margin: 0;
    padding: 2px;
    text-transform: uppercase;
    }

    .jp-SidePanel-toolbar {
    flex: 0 0 auto;
    }

    .jp-SidePanel-content {
    flex: 1 1 auto;
    }

    .jp-SidePanel-toolbar,
    .jp-AccordionPanel-toolbar {
    height: var(--jp-private-toolbar-height);
    }

    .jp-SidePanel-toolbar.jp-Toolbar-micro {
    display: none;
    }

    .lm-AccordionPanel .jp-AccordionPanel-title {
    box-sizing: border-box;
    line-height: 25px;
    margin: 0;
    display: flex;
    align-items: center;
    background: var(--jp-layout-color1);
    color: var(--jp-ui-font-color1);
    border-bottom: var(--jp-border-width) solid var(--jp-toolbar-border-color);
    box-shadow: var(--jp-toolbar-box-shadow);
    font-size: var(--jp-ui-font-size0);
    }

    .jp-AccordionPanel-title {
    cursor: pointer;
    user-select: none;
    -moz-user-select: none;
    -webkit-user-select: none;
    text-transform: uppercase;
    }

    .lm-AccordionPanel[data-orientation='horizontal'] > .jp-AccordionPanel-title {
    /* Title is rotated for horizontal accordion panel using CSS */
    display: block;
    transform-origin: top left;
    transform: rotate(-90deg) translate(-100%);
    }

    .jp-AccordionPanel-title .lm-AccordionPanel-titleLabel {
    user-select: none;
    text-overflow: ellipsis;
    white-space: nowrap;
    overflow: hidden;
    }

    .jp-AccordionPanel-title .lm-AccordionPanel-titleCollapser {
    transform: rotate(-90deg);
    margin: auto 0;
    height: 16px;
    }

    .jp-AccordionPanel-title.lm-mod-expanded .lm-AccordionPanel-titleCollapser {
    transform: rotate(0deg);
    }

    .lm-AccordionPanel .jp-AccordionPanel-toolbar {
    background: none;
    box-shadow: none;
    border: none;
    margin-left: auto;
    }

    .lm-AccordionPanel .lm-SplitPanel-handle:hover {
    background: var(--jp-layout-color3);
    }

    .jp-text-truncated {
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) 2017, Jupyter Development Team.
    |
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    .jp-Spinner {
    position: absolute;
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 10;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background: var(--jp-layout-color0);
    outline: none;
    }

    .jp-SpinnerContent {
    font-size: 10px;
    margin: 50px auto;
    text-indent: -9999em;
    width: 3em;
    height: 3em;
    border-radius: 50%;
    background: var(--jp-brand-color3);
    background: linear-gradient(
        to right,
        #f37626 10%,
        rgba(255, 255, 255, 0) 42%
    );
    position: relative;
    animation: load3 1s infinite linear, fadeIn 1s;
    }

    .jp-SpinnerContent::before {
    width: 50%;
    height: 50%;
    background: #f37626;
    border-radius: 100% 0 0;
    position: absolute;
    top: 0;
    left: 0;
    content: '';
    }

    .jp-SpinnerContent::after {
    background: var(--jp-layout-color0);
    width: 75%;
    height: 75%;
    border-radius: 50%;
    content: '';
    margin: auto;
    position: absolute;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    }

    @keyframes fadeIn {
    0% {
        opacity: 0;
    }

    100% {
        opacity: 1;
    }
    }

    @keyframes load3 {
    0% {
        transform: rotate(0deg);
    }

    100% {
        transform: rotate(360deg);
    }
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) 2014-2017, Jupyter Development Team.
    |
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    button.jp-mod-styled {
    font-size: var(--jp-ui-font-size1);
    color: var(--jp-ui-font-color0);
    border: none;
    box-sizing: border-box;
    text-align: center;
    line-height: 32px;
    height: 32px;
    padding: 0 12px;
    letter-spacing: 0.8px;
    outline: none;
    appearance: none;
    -webkit-appearance: none;
    -moz-appearance: none;
    }

    input.jp-mod-styled {
    background: var(--jp-input-background);
    height: 28px;
    box-sizing: border-box;
    border: var(--jp-border-width) solid var(--jp-border-color1);
    padding-left: 7px;
    padding-right: 7px;
    font-size: var(--jp-ui-font-size2);
    color: var(--jp-ui-font-color0);
    outline: none;
    appearance: none;
    -webkit-appearance: none;
    -moz-appearance: none;
    }

    input[type='checkbox'].jp-mod-styled {
    appearance: checkbox;
    -webkit-appearance: checkbox;
    -moz-appearance: checkbox;
    height: auto;
    }

    input.jp-mod-styled:focus {
    border: var(--jp-border-width) solid var(--md-blue-500);
    box-shadow: inset 0 0 4px var(--md-blue-300);
    }

    .jp-select-wrapper {
    display: flex;
    position: relative;
    flex-direction: column;
    padding: 1px;
    background-color: var(--jp-layout-color1);
    box-sizing: border-box;
    margin-bottom: 12px;
    }

    .jp-select-wrapper:not(.multiple) {
    height: 28px;
    }

    .jp-select-wrapper.jp-mod-focused select.jp-mod-styled {
    border: var(--jp-border-width) solid var(--jp-input-active-border-color);
    box-shadow: var(--jp-input-box-shadow);
    background-color: var(--jp-input-active-background);
    }

    select.jp-mod-styled:hover {
    cursor: pointer;
    color: var(--jp-ui-font-color0);
    background-color: var(--jp-input-hover-background);
    box-shadow: inset 0 0 1px rgba(0, 0, 0, 0.5);
    }

    select.jp-mod-styled {
    flex: 1 1 auto;
    width: 100%;
    font-size: var(--jp-ui-font-size2);
    background: var(--jp-input-background);
    color: var(--jp-ui-font-color0);
    padding: 0 25px 0 8px;
    border: var(--jp-border-width) solid var(--jp-input-border-color);
    border-radius: 0;
    outline: none;
    appearance: none;
    -webkit-appearance: none;
    -moz-appearance: none;
    }

    select.jp-mod-styled:not([multiple]) {
    height: 32px;
    }

    select.jp-mod-styled[multiple] {
    max-height: 200px;
    overflow-y: auto;
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    .jp-switch {
    display: flex;
    align-items: center;
    padding-left: 4px;
    padding-right: 4px;
    font-size: var(--jp-ui-font-size1);
    background-color: transparent;
    color: var(--jp-ui-font-color1);
    border: none;
    height: 20px;
    }

    .jp-switch:hover {
    background-color: var(--jp-layout-color2);
    }

    .jp-switch-label {
    margin-right: 5px;
    font-family: var(--jp-ui-font-family);
    }

    .jp-switch-track {
    cursor: pointer;
    background-color: var(--jp-switch-color, var(--jp-border-color1));
    -webkit-transition: 0.4s;
    transition: 0.4s;
    border-radius: 34px;
    height: 16px;
    width: 35px;
    position: relative;
    }

    .jp-switch-track::before {
    content: '';
    position: absolute;
    height: 10px;
    width: 10px;
    margin: 3px;
    left: 0;
    background-color: var(--jp-ui-inverse-font-color1);
    -webkit-transition: 0.4s;
    transition: 0.4s;
    border-radius: 50%;
    }

    .jp-switch[aria-checked='true'] .jp-switch-track {
    background-color: var(--jp-switch-true-position-color, var(--jp-warn-color0));
    }

    .jp-switch[aria-checked='true'] .jp-switch-track::before {
    /* track width (35) - margins (3 + 3) - thumb width (10) */
    left: 19px;
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) 2014-2016, Jupyter Development Team.
    |
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    :root {
    --jp-private-toolbar-height: calc(
        28px + var(--jp-border-width)
    ); /* leave 28px for content */
    }

    .jp-Toolbar {
    color: var(--jp-ui-font-color1);
    flex: 0 0 auto;
    display: flex;
    flex-direction: row;
    border-bottom: var(--jp-border-width) solid var(--jp-toolbar-border-color);
    box-shadow: var(--jp-toolbar-box-shadow);
    background: var(--jp-toolbar-background);
    min-height: var(--jp-toolbar-micro-height);
    padding: 2px;
    z-index: 8;
    overflow-x: hidden;
    }

    /* Toolbar items */

    .jp-Toolbar > .jp-Toolbar-item.jp-Toolbar-spacer {
    flex-grow: 1;
    flex-shrink: 1;
    }

    .jp-Toolbar-item.jp-Toolbar-kernelStatus {
    display: inline-block;
    width: 32px;
    background-repeat: no-repeat;
    background-position: center;
    background-size: 16px;
    }

    .jp-Toolbar > .jp-Toolbar-item {
    flex: 0 0 auto;
    display: flex;
    padding-left: 1px;
    padding-right: 1px;
    font-size: var(--jp-ui-font-size1);
    line-height: var(--jp-private-toolbar-height);
    height: 100%;
    }

    /* Toolbar buttons */

    /* This is the div we use to wrap the react component into a Widget */
    div.jp-ToolbarButton {
    color: transparent;
    border: none;
    box-sizing: border-box;
    outline: none;
    appearance: none;
    -webkit-appearance: none;
    -moz-appearance: none;
    padding: 0;
    margin: 0;
    }

    button.jp-ToolbarButtonComponent {
    background: var(--jp-layout-color1);
    border: none;
    box-sizing: border-box;
    outline: none;
    appearance: none;
    -webkit-appearance: none;
    -moz-appearance: none;
    padding: 0 6px;
    margin: 0;
    height: 24px;
    border-radius: var(--jp-border-radius);
    display: flex;
    align-items: center;
    text-align: center;
    font-size: 14px;
    min-width: unset;
    min-height: unset;
    }

    button.jp-ToolbarButtonComponent:disabled {
    opacity: 0.4;
    }

    button.jp-ToolbarButtonComponent > span {
    padding: 0;
    flex: 0 0 auto;
    }

    button.jp-ToolbarButtonComponent .jp-ToolbarButtonComponent-label {
    font-size: var(--jp-ui-font-size1);
    line-height: 100%;
    padding-left: 2px;
    color: var(--jp-ui-font-color1);
    font-family: var(--jp-ui-font-family);
    }

    #jp-main-dock-panel[data-mode='single-document']
    .jp-MainAreaWidget
    > .jp-Toolbar.jp-Toolbar-micro {
    padding: 0;
    min-height: 0;
    }

    #jp-main-dock-panel[data-mode='single-document']
    .jp-MainAreaWidget
    > .jp-Toolbar {
    border: none;
    box-shadow: none;
    }

    /*
    * Copyright (c) Jupyter Development Team.
    * Distributed under the terms of the Modified BSD License.
    */

    .jp-WindowedPanel-outer {
    position: relative;
    overflow-y: auto;
    }

    .jp-WindowedPanel-inner {
    position: relative;
    }

    .jp-WindowedPanel-window {
    position: absolute;
    left: 0;
    right: 0;
    overflow: visible;
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    /* Sibling imports */

    body {
    color: var(--jp-ui-font-color1);
    font-size: var(--jp-ui-font-size1);
    }

    /* Disable native link decoration styles everywhere outside of dialog boxes */
    a {
    text-decoration: unset;
    color: unset;
    }

    a:hover {
    text-decoration: unset;
    color: unset;
    }

    /* Accessibility for links inside dialog box text */
    .jp-Dialog-content a {
    text-decoration: revert;
    color: var(--jp-content-link-color);
    }

    .jp-Dialog-content a:hover {
    text-decoration: revert;
    }

    /* Styles for ui-components */
    .jp-Button {
    color: var(--jp-ui-font-color2);
    border-radius: var(--jp-border-radius);
    padding: 0 12px;
    font-size: var(--jp-ui-font-size1);

    /* Copy from blueprint 3 */
    display: inline-flex;
    flex-direction: row;
    border: none;
    cursor: pointer;
    align-items: center;
    justify-content: center;
    text-align: left;
    vertical-align: middle;
    min-height: 30px;
    min-width: 30px;
    }

    .jp-Button:disabled {
    cursor: not-allowed;
    }

    .jp-Button:empty {
    padding: 0 !important;
    }

    .jp-Button.jp-mod-small {
    min-height: 24px;
    min-width: 24px;
    font-size: 12px;
    padding: 0 7px;
    }

    /* Use our own theme for hover styles */
    .jp-Button.jp-mod-minimal:hover {
    background-color: var(--jp-layout-color2);
    }

    .jp-Button.jp-mod-minimal {
    background: none;
    }

    .jp-InputGroup {
    display: block;
    position: relative;
    }

    .jp-InputGroup input {
    box-sizing: border-box;
    border: none;
    border-radius: 0;
    background-color: transparent;
    color: var(--jp-ui-font-color0);
    box-shadow: inset 0 0 0 var(--jp-border-width) var(--jp-input-border-color);
    padding-bottom: 0;
    padding-top: 0;
    padding-left: 10px;
    padding-right: 28px;
    position: relative;
    width: 100%;
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    font-size: 14px;
    font-weight: 400;
    height: 30px;
    line-height: 30px;
    outline: none;
    vertical-align: middle;
    }

    .jp-InputGroup input:focus {
    box-shadow: inset 0 0 0 var(--jp-border-width)
        var(--jp-input-active-box-shadow-color),
        inset 0 0 0 3px var(--jp-input-active-box-shadow-color);
    }

    .jp-InputGroup input:disabled {
    cursor: not-allowed;
    resize: block;
    background-color: var(--jp-layout-color2);
    color: var(--jp-ui-font-color2);
    }

    .jp-InputGroup input:disabled ~ span {
    cursor: not-allowed;
    color: var(--jp-ui-font-color2);
    }

    .jp-InputGroup input::placeholder,
    input::placeholder {
    color: var(--jp-ui-font-color2);
    }

    .jp-InputGroupAction {
    position: absolute;
    bottom: 1px;
    right: 0;
    padding: 6px;
    }

    .jp-HTMLSelect.jp-DefaultStyle select {
    background-color: initial;
    border: none;
    border-radius: 0;
    box-shadow: none;
    color: var(--jp-ui-font-color0);
    display: block;
    font-size: var(--jp-ui-font-size1);
    font-family: var(--jp-ui-font-family);
    height: 24px;
    line-height: 14px;
    padding: 0 25px 0 10px;
    text-align: left;
    -moz-appearance: none;
    -webkit-appearance: none;
    }

    .jp-HTMLSelect.jp-DefaultStyle select:disabled {
    background-color: var(--jp-layout-color2);
    color: var(--jp-ui-font-color2);
    cursor: not-allowed;
    resize: block;
    }

    .jp-HTMLSelect.jp-DefaultStyle select:disabled ~ span {
    cursor: not-allowed;
    }

    /* Use our own theme for hover and option styles */
    /* stylelint-disable-next-line selector-max-type */
    .jp-HTMLSelect.jp-DefaultStyle select:hover,
    .jp-HTMLSelect.jp-DefaultStyle select > option {
    background-color: var(--jp-layout-color2);
    color: var(--jp-ui-font-color0);
    }

    select {
    box-sizing: border-box;
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    /*-----------------------------------------------------------------------------
    | Styles
    |----------------------------------------------------------------------------*/

    .jp-StatusBar-Widget {
    display: flex;
    align-items: center;
    background: var(--jp-layout-color2);
    min-height: var(--jp-statusbar-height);
    justify-content: space-between;
    padding: 0 10px;
    }

    .jp-StatusBar-Left {
    display: flex;
    align-items: center;
    flex-direction: row;
    }

    .jp-StatusBar-Middle {
    display: flex;
    align-items: center;
    }

    .jp-StatusBar-Right {
    display: flex;
    align-items: center;
    flex-direction: row-reverse;
    }

    .jp-StatusBar-Item {
    max-height: var(--jp-statusbar-height);
    margin: 0 2px;
    height: var(--jp-statusbar-height);
    white-space: nowrap;
    text-overflow: ellipsis;
    color: var(--jp-ui-font-color1);
    padding: 0 6px;
    }

    .jp-mod-highlighted:hover {
    background-color: var(--jp-layout-color3);
    }

    .jp-mod-clicked {
    background-color: var(--jp-brand-color1);
    }

    .jp-mod-clicked:hover {
    background-color: var(--jp-brand-color0);
    }

    .jp-mod-clicked .jp-StatusBar-TextItem {
    color: var(--jp-ui-inverse-font-color1);
    }

    .jp-StatusBar-HoverItem {
    box-shadow: '0px 4px 4px rgba(0, 0, 0, 0.25)';
    }

    .jp-StatusBar-TextItem {
    font-size: var(--jp-ui-font-size1);
    font-family: var(--jp-ui-font-family);
    line-height: 24px;
    color: var(--jp-ui-font-color1);
    }

    .jp-StatusBar-GroupItem {
    display: flex;
    align-items: center;
    flex-direction: row;
    }

    .jp-Statusbar-ProgressCircle svg {
    display: block;
    margin: 0 auto;
    width: 16px;
    height: 24px;
    align-self: normal;
    }

    .jp-Statusbar-ProgressCircle path {
    fill: var(--jp-inverse-layout-color3);
    }

    .jp-Statusbar-ProgressBar-progress-bar {
    height: 10px;
    width: 100px;
    border: solid 0.25px var(--jp-brand-color2);
    border-radius: 3px;
    overflow: hidden;
    align-self: center;
    }

    .jp-Statusbar-ProgressBar-progress-bar > div {
    background-color: var(--jp-brand-color2);
    background-image: linear-gradient(
        -45deg,
        rgba(255, 255, 255, 0.2) 25%,
        transparent 25%,
        transparent 50%,
        rgba(255, 255, 255, 0.2) 50%,
        rgba(255, 255, 255, 0.2) 75%,
        transparent 75%,
        transparent
    );
    background-size: 40px 40px;
    float: left;
    width: 0%;
    height: 100%;
    font-size: 12px;
    line-height: 14px;
    color: #fff;
    text-align: center;
    animation: jp-Statusbar-ExecutionTime-progress-bar 2s linear infinite;
    }

    .jp-Statusbar-ProgressBar-progress-bar p {
    color: var(--jp-ui-font-color1);
    font-family: var(--jp-ui-font-family);
    font-size: var(--jp-ui-font-size1);
    line-height: 10px;
    width: 100px;
    }

    @keyframes jp-Statusbar-ExecutionTime-progress-bar {
    0% {
        background-position: 0 0;
    }

    100% {
        background-position: 40px 40px;
    }
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    /*-----------------------------------------------------------------------------
    | Variables
    |----------------------------------------------------------------------------*/

    :root {
    --jp-private-commandpalette-search-height: 28px;
    }

    /*-----------------------------------------------------------------------------
    | Overall styles
    |----------------------------------------------------------------------------*/

    .lm-CommandPalette {
    padding-bottom: 0;
    color: var(--jp-ui-font-color1);
    background: var(--jp-layout-color1);

    /* This is needed so that all font sizing of children done in ems is
    * relative to this base size */
    font-size: var(--jp-ui-font-size1);
    }

    /*-----------------------------------------------------------------------------
    | Modal variant
    |----------------------------------------------------------------------------*/

    .jp-ModalCommandPalette {
    position: absolute;
    z-index: 10000;
    top: 38px;
    left: 30%;
    margin: 0;
    padding: 4px;
    width: 40%;
    box-shadow: var(--jp-elevation-z4);
    border-radius: 4px;
    background: var(--jp-layout-color0);
    }

    .jp-ModalCommandPalette .lm-CommandPalette {
    max-height: 40vh;
    }

    .jp-ModalCommandPalette .lm-CommandPalette .lm-close-icon::after {
    display: none;
    }

    .jp-ModalCommandPalette .lm-CommandPalette .lm-CommandPalette-header {
    display: none;
    }

    .jp-ModalCommandPalette .lm-CommandPalette .lm-CommandPalette-item {
    margin-left: 4px;
    margin-right: 4px;
    }

    .jp-ModalCommandPalette
    .lm-CommandPalette
    .lm-CommandPalette-item.lm-mod-disabled {
    display: none;
    }

    /*-----------------------------------------------------------------------------
    | Search
    |----------------------------------------------------------------------------*/

    .lm-CommandPalette-search {
    padding: 4px;
    background-color: var(--jp-layout-color1);
    z-index: 2;
    }

    .lm-CommandPalette-wrapper {
    overflow: overlay;
    padding: 0 9px;
    background-color: var(--jp-input-active-background);
    height: 30px;
    box-shadow: inset 0 0 0 var(--jp-border-width) var(--jp-input-border-color);
    }

    .lm-CommandPalette.lm-mod-focused .lm-CommandPalette-wrapper {
    box-shadow: inset 0 0 0 1px var(--jp-input-active-box-shadow-color),
        inset 0 0 0 3px var(--jp-input-active-box-shadow-color);
    }

    .jp-SearchIconGroup {
    color: white;
    background-color: var(--jp-brand-color1);
    position: absolute;
    top: 4px;
    right: 4px;
    padding: 5px 5px 1px;
    }

    .jp-SearchIconGroup svg {
    height: 20px;
    width: 20px;
    }

    .jp-SearchIconGroup .jp-icon3[fill] {
    fill: var(--jp-layout-color0);
    }

    .lm-CommandPalette-input {
    background: transparent;
    width: calc(100% - 18px);
    float: left;
    border: none;
    outline: none;
    font-size: var(--jp-ui-font-size1);
    color: var(--jp-ui-font-color0);
    line-height: var(--jp-private-commandpalette-search-height);
    }

    .lm-CommandPalette-input::-webkit-input-placeholder,
    .lm-CommandPalette-input::-moz-placeholder,
    .lm-CommandPalette-input:-ms-input-placeholder {
    color: var(--jp-ui-font-color2);
    font-size: var(--jp-ui-font-size1);
    }

    /*-----------------------------------------------------------------------------
    | Results
    |----------------------------------------------------------------------------*/

    .lm-CommandPalette-header:first-child {
    margin-top: 0;
    }

    .lm-CommandPalette-header {
    border-bottom: solid var(--jp-border-width) var(--jp-border-color2);
    color: var(--jp-ui-font-color1);
    cursor: pointer;
    display: flex;
    font-size: var(--jp-ui-font-size0);
    font-weight: 600;
    letter-spacing: 1px;
    margin-top: 8px;
    padding: 8px 0 8px 12px;
    text-transform: uppercase;
    }

    .lm-CommandPalette-header.lm-mod-active {
    background: var(--jp-layout-color2);
    }

    .lm-CommandPalette-header > mark {
    background-color: transparent;
    font-weight: bold;
    color: var(--jp-ui-font-color1);
    }

    .lm-CommandPalette-item {
    padding: 4px 12px 4px 4px;
    color: var(--jp-ui-font-color1);
    font-size: var(--jp-ui-font-size1);
    font-weight: 400;
    display: flex;
    }

    .lm-CommandPalette-item.lm-mod-disabled {
    color: var(--jp-ui-font-color2);
    }

    .lm-CommandPalette-item.lm-mod-active {
    color: var(--jp-ui-inverse-font-color1);
    background: var(--jp-brand-color1);
    }

    .lm-CommandPalette-item.lm-mod-active .lm-CommandPalette-itemLabel > mark {
    color: var(--jp-ui-inverse-font-color0);
    }

    .lm-CommandPalette-item.lm-mod-active .jp-icon-selectable[fill] {
    fill: var(--jp-layout-color0);
    }

    .lm-CommandPalette-item.lm-mod-active:hover:not(.lm-mod-disabled) {
    color: var(--jp-ui-inverse-font-color1);
    background: var(--jp-brand-color1);
    }

    .lm-CommandPalette-item:hover:not(.lm-mod-active):not(.lm-mod-disabled) {
    background: var(--jp-layout-color2);
    }

    .lm-CommandPalette-itemContent {
    overflow: hidden;
    }

    .lm-CommandPalette-itemLabel > mark {
    color: var(--jp-ui-font-color0);
    background-color: transparent;
    font-weight: bold;
    }

    .lm-CommandPalette-item.lm-mod-disabled mark {
    color: var(--jp-ui-font-color2);
    }

    .lm-CommandPalette-item .lm-CommandPalette-itemIcon {
    margin: 0 4px 0 0;
    position: relative;
    width: 16px;
    top: 2px;
    flex: 0 0 auto;
    }

    .lm-CommandPalette-item.lm-mod-disabled .lm-CommandPalette-itemIcon {
    opacity: 0.6;
    }

    .lm-CommandPalette-item .lm-CommandPalette-itemShortcut {
    flex: 0 0 auto;
    }

    .lm-CommandPalette-itemCaption {
    display: none;
    }

    .lm-CommandPalette-content {
    background-color: var(--jp-layout-color1);
    }

    .lm-CommandPalette-content:empty::after {
    content: 'No results';
    margin: auto;
    margin-top: 20px;
    width: 100px;
    display: block;
    font-size: var(--jp-ui-font-size2);
    font-family: var(--jp-ui-font-family);
    font-weight: lighter;
    }

    .lm-CommandPalette-emptyMessage {
    text-align: center;
    margin-top: 24px;
    line-height: 1.32;
    padding: 0 8px;
    color: var(--jp-content-font-color3);
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) 2014-2017, Jupyter Development Team.
    |
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    .jp-Dialog {
    position: absolute;
    z-index: 10000;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    top: 0;
    left: 0;
    margin: 0;
    padding: 0;
    width: 100%;
    height: 100%;
    background: var(--jp-dialog-background);
    }

    .jp-Dialog-content {
    display: flex;
    flex-direction: column;
    margin-left: auto;
    margin-right: auto;
    background: var(--jp-layout-color1);
    padding: 24px 24px 12px;
    min-width: 300px;
    min-height: 150px;
    max-width: 1000px;
    max-height: 500px;
    box-sizing: border-box;
    box-shadow: var(--jp-elevation-z20);
    word-wrap: break-word;
    border-radius: var(--jp-border-radius);

    /* This is needed so that all font sizing of children done in ems is
    * relative to this base size */
    font-size: var(--jp-ui-font-size1);
    color: var(--jp-ui-font-color1);
    resize: both;
    }

    .jp-Dialog-content.jp-Dialog-content-small {
    max-width: 500px;
    }

    .jp-Dialog-button {
    overflow: visible;
    }

    button.jp-Dialog-button:focus {
    outline: 1px solid var(--jp-brand-color1);
    outline-offset: 4px;
    -moz-outline-radius: 0;
    }

    button.jp-Dialog-button:focus::-moz-focus-inner {
    border: 0;
    }

    button.jp-Dialog-button.jp-mod-styled.jp-mod-accept:focus,
    button.jp-Dialog-button.jp-mod-styled.jp-mod-warn:focus,
    button.jp-Dialog-button.jp-mod-styled.jp-mod-reject:focus {
    outline-offset: 4px;
    -moz-outline-radius: 0;
    }

    button.jp-Dialog-button.jp-mod-styled.jp-mod-accept:focus {
    outline: 1px solid var(--jp-accept-color-normal, var(--jp-brand-color1));
    }

    button.jp-Dialog-button.jp-mod-styled.jp-mod-warn:focus {
    outline: 1px solid var(--jp-warn-color-normal, var(--jp-error-color1));
    }

    button.jp-Dialog-button.jp-mod-styled.jp-mod-reject:focus {
    outline: 1px solid var(--jp-reject-color-normal, var(--md-grey-600));
    }

    button.jp-Dialog-close-button {
    padding: 0;
    height: 100%;
    min-width: unset;
    min-height: unset;
    }

    .jp-Dialog-header {
    display: flex;
    justify-content: space-between;
    flex: 0 0 auto;
    padding-bottom: 12px;
    font-size: var(--jp-ui-font-size3);
    font-weight: 400;
    color: var(--jp-ui-font-color1);
    }

    .jp-Dialog-body {
    display: flex;
    flex-direction: column;
    flex: 1 1 auto;
    font-size: var(--jp-ui-font-size1);
    background: var(--jp-layout-color1);
    color: var(--jp-ui-font-color1);
    overflow: auto;
    }

    .jp-Dialog-footer {
    display: flex;
    flex-direction: row;
    justify-content: flex-end;
    align-items: center;
    flex: 0 0 auto;
    margin-left: -12px;
    margin-right: -12px;
    padding: 12px;
    }

    .jp-Dialog-checkbox {
    padding-right: 5px;
    }

    .jp-Dialog-checkbox > input:focus-visible {
    outline: 1px solid var(--jp-input-active-border-color);
    outline-offset: 1px;
    }

    .jp-Dialog-spacer {
    flex: 1 1 auto;
    }

    .jp-Dialog-title {
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
    }

    .jp-Dialog-body > .jp-select-wrapper {
    width: 100%;
    }

    .jp-Dialog-body > button {
    padding: 0 16px;
    }

    .jp-Dialog-body > label {
    line-height: 1.4;
    color: var(--jp-ui-font-color0);
    }

    .jp-Dialog-button.jp-mod-styled:not(:last-child) {
    margin-right: 12px;
    }

    /*
    * Copyright (c) Jupyter Development Team.
    * Distributed under the terms of the Modified BSD License.
    */

    .jp-Input-Boolean-Dialog {
    flex-direction: row-reverse;
    align-items: end;
    width: 100%;
    }

    .jp-Input-Boolean-Dialog > label {
    flex: 1 1 auto;
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) 2014-2016, Jupyter Development Team.
    |
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    .jp-MainAreaWidget > :focus {
    outline: none;
    }

    .jp-MainAreaWidget .jp-MainAreaWidget-error {
    padding: 6px;
    }

    .jp-MainAreaWidget .jp-MainAreaWidget-error > pre {
    width: auto;
    padding: 10px;
    background: var(--jp-error-color3);
    border: var(--jp-border-width) solid var(--jp-error-color1);
    border-radius: var(--jp-border-radius);
    color: var(--jp-ui-font-color1);
    font-size: var(--jp-ui-font-size1);
    white-space: pre-wrap;
    word-wrap: break-word;
    }

    /*
    * Copyright (c) Jupyter Development Team.
    * Distributed under the terms of the Modified BSD License.
    */

    /**
    * google-material-color v1.2.6
    * https://github.com/danlevan/google-material-color
    */
    :root {
    --md-red-50: #ffebee;
    --md-red-100: #ffcdd2;
    --md-red-200: #ef9a9a;
    --md-red-300: #e57373;
    --md-red-400: #ef5350;
    --md-red-500: #f44336;
    --md-red-600: #e53935;
    --md-red-700: #d32f2f;
    --md-red-800: #c62828;
    --md-red-900: #b71c1c;
    --md-red-A100: #ff8a80;
    --md-red-A200: #ff5252;
    --md-red-A400: #ff1744;
    --md-red-A700: #d50000;
    --md-pink-50: #fce4ec;
    --md-pink-100: #f8bbd0;
    --md-pink-200: #f48fb1;
    --md-pink-300: #f06292;
    --md-pink-400: #ec407a;
    --md-pink-500: #e91e63;
    --md-pink-600: #d81b60;
    --md-pink-700: #c2185b;
    --md-pink-800: #ad1457;
    --md-pink-900: #880e4f;
    --md-pink-A100: #ff80ab;
    --md-pink-A200: #ff4081;
    --md-pink-A400: #f50057;
    --md-pink-A700: #c51162;
    --md-purple-50: #f3e5f5;
    --md-purple-100: #e1bee7;
    --md-purple-200: #ce93d8;
    --md-purple-300: #ba68c8;
    --md-purple-400: #ab47bc;
    --md-purple-500: #9c27b0;
    --md-purple-600: #8e24aa;
    --md-purple-700: #7b1fa2;
    --md-purple-800: #6a1b9a;
    --md-purple-900: #4a148c;
    --md-purple-A100: #ea80fc;
    --md-purple-A200: #e040fb;
    --md-purple-A400: #d500f9;
    --md-purple-A700: #a0f;
    --md-deep-purple-50: #ede7f6;
    --md-deep-purple-100: #d1c4e9;
    --md-deep-purple-200: #b39ddb;
    --md-deep-purple-300: #9575cd;
    --md-deep-purple-400: #7e57c2;
    --md-deep-purple-500: #673ab7;
    --md-deep-purple-600: #5e35b1;
    --md-deep-purple-700: #512da8;
    --md-deep-purple-800: #4527a0;
    --md-deep-purple-900: #311b92;
    --md-deep-purple-A100: #b388ff;
    --md-deep-purple-A200: #7c4dff;
    --md-deep-purple-A400: #651fff;
    --md-deep-purple-A700: #6200ea;
    --md-indigo-50: #e8eaf6;
    --md-indigo-100: #c5cae9;
    --md-indigo-200: #9fa8da;
    --md-indigo-300: #7986cb;
    --md-indigo-400: #5c6bc0;
    --md-indigo-500: #3f51b5;
    --md-indigo-600: #3949ab;
    --md-indigo-700: #303f9f;
    --md-indigo-800: #283593;
    --md-indigo-900: #1a237e;
    --md-indigo-A100: #8c9eff;
    --md-indigo-A200: #536dfe;
    --md-indigo-A400: #3d5afe;
    --md-indigo-A700: #304ffe;
    --md-blue-50: #e3f2fd;
    --md-blue-100: #bbdefb;
    --md-blue-200: #90caf9;
    --md-blue-300: #64b5f6;
    --md-blue-400: #42a5f5;
    --md-blue-500: #2196f3;
    --md-blue-600: #1e88e5;
    --md-blue-700: #1976d2;
    --md-blue-800: #1565c0;
    --md-blue-900: #0d47a1;
    --md-blue-A100: #82b1ff;
    --md-blue-A200: #448aff;
    --md-blue-A400: #2979ff;
    --md-blue-A700: #2962ff;
    --md-light-blue-50: #e1f5fe;
    --md-light-blue-100: #b3e5fc;
    --md-light-blue-200: #81d4fa;
    --md-light-blue-300: #4fc3f7;
    --md-light-blue-400: #29b6f6;
    --md-light-blue-500: #03a9f4;
    --md-light-blue-600: #039be5;
    --md-light-blue-700: #0288d1;
    --md-light-blue-800: #0277bd;
    --md-light-blue-900: #01579b;
    --md-light-blue-A100: #80d8ff;
    --md-light-blue-A200: #40c4ff;
    --md-light-blue-A400: #00b0ff;
    --md-light-blue-A700: #0091ea;
    --md-cyan-50: #e0f7fa;
    --md-cyan-100: #b2ebf2;
    --md-cyan-200: #80deea;
    --md-cyan-300: #4dd0e1;
    --md-cyan-400: #26c6da;
    --md-cyan-500: #00bcd4;
    --md-cyan-600: #00acc1;
    --md-cyan-700: #0097a7;
    --md-cyan-800: #00838f;
    --md-cyan-900: #006064;
    --md-cyan-A100: #84ffff;
    --md-cyan-A200: #18ffff;
    --md-cyan-A400: #00e5ff;
    --md-cyan-A700: #00b8d4;
    --md-teal-50: #e0f2f1;
    --md-teal-100: #b2dfdb;
    --md-teal-200: #80cbc4;
    --md-teal-300: #4db6ac;
    --md-teal-400: #26a69a;
    --md-teal-500: #009688;
    --md-teal-600: #00897b;
    --md-teal-700: #00796b;
    --md-teal-800: #00695c;
    --md-teal-900: #004d40;
    --md-teal-A100: #a7ffeb;
    --md-teal-A200: #64ffda;
    --md-teal-A400: #1de9b6;
    --md-teal-A700: #00bfa5;
    --md-green-50: #e8f5e9;
    --md-green-100: #c8e6c9;
    --md-green-200: #a5d6a7;
    --md-green-300: #81c784;
    --md-green-400: #66bb6a;
    --md-green-500: #4caf50;
    --md-green-600: #43a047;
    --md-green-700: #388e3c;
    --md-green-800: #2e7d32;
    --md-green-900: #1b5e20;
    --md-green-A100: #b9f6ca;
    --md-green-A200: #69f0ae;
    --md-green-A400: #00e676;
    --md-green-A700: #00c853;
    --md-light-green-50: #f1f8e9;
    --md-light-green-100: #dcedc8;
    --md-light-green-200: #c5e1a5;
    --md-light-green-300: #aed581;
    --md-light-green-400: #9ccc65;
    --md-light-green-500: #8bc34a;
    --md-light-green-600: #7cb342;
    --md-light-green-700: #689f38;
    --md-light-green-800: #558b2f;
    --md-light-green-900: #33691e;
    --md-light-green-A100: #ccff90;
    --md-light-green-A200: #b2ff59;
    --md-light-green-A400: #76ff03;
    --md-light-green-A700: #64dd17;
    --md-lime-50: #f9fbe7;
    --md-lime-100: #f0f4c3;
    --md-lime-200: #e6ee9c;
    --md-lime-300: #dce775;
    --md-lime-400: #d4e157;
    --md-lime-500: #cddc39;
    --md-lime-600: #c0ca33;
    --md-lime-700: #afb42b;
    --md-lime-800: #9e9d24;
    --md-lime-900: #827717;
    --md-lime-A100: #f4ff81;
    --md-lime-A200: #eeff41;
    --md-lime-A400: #c6ff00;
    --md-lime-A700: #aeea00;
    --md-yellow-50: #fffde7;
    --md-yellow-100: #fff9c4;
    --md-yellow-200: #fff59d;
    --md-yellow-300: #fff176;
    --md-yellow-400: #ffee58;
    --md-yellow-500: #ffeb3b;
    --md-yellow-600: #fdd835;
    --md-yellow-700: #fbc02d;
    --md-yellow-800: #f9a825;
    --md-yellow-900: #f57f17;
    --md-yellow-A100: #ffff8d;
    --md-yellow-A200: #ff0;
    --md-yellow-A400: #ffea00;
    --md-yellow-A700: #ffd600;
    --md-amber-50: #fff8e1;
    --md-amber-100: #ffecb3;
    --md-amber-200: #ffe082;
    --md-amber-300: #ffd54f;
    --md-amber-400: #ffca28;
    --md-amber-500: #ffc107;
    --md-amber-600: #ffb300;
    --md-amber-700: #ffa000;
    --md-amber-800: #ff8f00;
    --md-amber-900: #ff6f00;
    --md-amber-A100: #ffe57f;
    --md-amber-A200: #ffd740;
    --md-amber-A400: #ffc400;
    --md-amber-A700: #ffab00;
    --md-orange-50: #fff3e0;
    --md-orange-100: #ffe0b2;
    --md-orange-200: #ffcc80;
    --md-orange-300: #ffb74d;
    --md-orange-400: #ffa726;
    --md-orange-500: #ff9800;
    --md-orange-600: #fb8c00;
    --md-orange-700: #f57c00;
    --md-orange-800: #ef6c00;
    --md-orange-900: #e65100;
    --md-orange-A100: #ffd180;
    --md-orange-A200: #ffab40;
    --md-orange-A400: #ff9100;
    --md-orange-A700: #ff6d00;
    --md-deep-orange-50: #fbe9e7;
    --md-deep-orange-100: #ffccbc;
    --md-deep-orange-200: #ffab91;
    --md-deep-orange-300: #ff8a65;
    --md-deep-orange-400: #ff7043;
    --md-deep-orange-500: #ff5722;
    --md-deep-orange-600: #f4511e;
    --md-deep-orange-700: #e64a19;
    --md-deep-orange-800: #d84315;
    --md-deep-orange-900: #bf360c;
    --md-deep-orange-A100: #ff9e80;
    --md-deep-orange-A200: #ff6e40;
    --md-deep-orange-A400: #ff3d00;
    --md-deep-orange-A700: #dd2c00;
    --md-brown-50: #efebe9;
    --md-brown-100: #d7ccc8;
    --md-brown-200: #bcaaa4;
    --md-brown-300: #a1887f;
    --md-brown-400: #8d6e63;
    --md-brown-500: #795548;
    --md-brown-600: #6d4c41;
    --md-brown-700: #5d4037;
    --md-brown-800: #4e342e;
    --md-brown-900: #3e2723;
    --md-grey-50: #fafafa;
    --md-grey-100: #f5f5f5;
    --md-grey-200: #eee;
    --md-grey-300: #e0e0e0;
    --md-grey-400: #bdbdbd;
    --md-grey-500: #9e9e9e;
    --md-grey-600: #757575;
    --md-grey-700: #616161;
    --md-grey-800: #424242;
    --md-grey-900: #212121;
    --md-blue-grey-50: #eceff1;
    --md-blue-grey-100: #cfd8dc;
    --md-blue-grey-200: #b0bec5;
    --md-blue-grey-300: #90a4ae;
    --md-blue-grey-400: #78909c;
    --md-blue-grey-500: #607d8b;
    --md-blue-grey-600: #546e7a;
    --md-blue-grey-700: #455a64;
    --md-blue-grey-800: #37474f;
    --md-blue-grey-900: #263238;
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) 2014-2017, Jupyter Development Team.
    |
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    /*-----------------------------------------------------------------------------
    | RenderedText
    |----------------------------------------------------------------------------*/

    :root {
    /* This is the padding value to fill the gaps between lines containing spans with background color. */
    --jp-private-code-span-padding: calc(
        (var(--jp-code-line-height) - 1) * var(--jp-code-font-size) / 2
    );
    }

    .jp-RenderedText {
    text-align: left;
    padding-left: var(--jp-code-padding);
    line-height: var(--jp-code-line-height);
    font-family: var(--jp-code-font-family);
    }

    .jp-RenderedText pre,
    .jp-RenderedJavaScript pre,
    .jp-RenderedHTMLCommon pre {
    color: var(--jp-content-font-color1);
    font-size: var(--jp-code-font-size);
    border: none;
    margin: 0;
    padding: 0;
    }

    .jp-RenderedText pre a:link {
    text-decoration: none;
    color: var(--jp-content-link-color);
    }

    .jp-RenderedText pre a:hover {
    text-decoration: underline;
    color: var(--jp-content-link-color);
    }

    .jp-RenderedText pre a:visited {
    text-decoration: none;
    color: var(--jp-content-link-color);
    }

    /* console foregrounds and backgrounds */
    .jp-RenderedText pre .ansi-black-fg {
    color: #3e424d;
    }

    .jp-RenderedText pre .ansi-red-fg {
    color: #e75c58;
    }

    .jp-RenderedText pre .ansi-green-fg {
    color: #00a250;
    }

    .jp-RenderedText pre .ansi-yellow-fg {
    color: #ddb62b;
    }

    .jp-RenderedText pre .ansi-blue-fg {
    color: #208ffb;
    }

    .jp-RenderedText pre .ansi-magenta-fg {
    color: #d160c4;
    }

    .jp-RenderedText pre .ansi-cyan-fg {
    color: #60c6c8;
    }

    .jp-RenderedText pre .ansi-white-fg {
    color: #c5c1b4;
    }

    .jp-RenderedText pre .ansi-black-bg {
    background-color: #3e424d;
    padding: var(--jp-private-code-span-padding) 0;
    }

    .jp-RenderedText pre .ansi-red-bg {
    background-color: #e75c58;
    padding: var(--jp-private-code-span-padding) 0;
    }

    .jp-RenderedText pre .ansi-green-bg {
    background-color: #00a250;
    padding: var(--jp-private-code-span-padding) 0;
    }

    .jp-RenderedText pre .ansi-yellow-bg {
    background-color: #ddb62b;
    padding: var(--jp-private-code-span-padding) 0;
    }

    .jp-RenderedText pre .ansi-blue-bg {
    background-color: #208ffb;
    padding: var(--jp-private-code-span-padding) 0;
    }

    .jp-RenderedText pre .ansi-magenta-bg {
    background-color: #d160c4;
    padding: var(--jp-private-code-span-padding) 0;
    }

    .jp-RenderedText pre .ansi-cyan-bg {
    background-color: #60c6c8;
    padding: var(--jp-private-code-span-padding) 0;
    }

    .jp-RenderedText pre .ansi-white-bg {
    background-color: #c5c1b4;
    padding: var(--jp-private-code-span-padding) 0;
    }

    .jp-RenderedText pre .ansi-black-intense-fg {
    color: #282c36;
    }

    .jp-RenderedText pre .ansi-red-intense-fg {
    color: #b22b31;
    }

    .jp-RenderedText pre .ansi-green-intense-fg {
    color: #007427;
    }

    .jp-RenderedText pre .ansi-yellow-intense-fg {
    color: #b27d12;
    }

    .jp-RenderedText pre .ansi-blue-intense-fg {
    color: #0065ca;
    }

    .jp-RenderedText pre .ansi-magenta-intense-fg {
    color: #a03196;
    }

    .jp-RenderedText pre .ansi-cyan-intense-fg {
    color: #258f8f;
    }

    .jp-RenderedText pre .ansi-white-intense-fg {
    color: #a1a6b2;
    }

    .jp-RenderedText pre .ansi-black-intense-bg {
    background-color: #282c36;
    padding: var(--jp-private-code-span-padding) 0;
    }

    .jp-RenderedText pre .ansi-red-intense-bg {
    background-color: #b22b31;
    padding: var(--jp-private-code-span-padding) 0;
    }

    .jp-RenderedText pre .ansi-green-intense-bg {
    background-color: #007427;
    padding: var(--jp-private-code-span-padding) 0;
    }

    .jp-RenderedText pre .ansi-yellow-intense-bg {
    background-color: #b27d12;
    padding: var(--jp-private-code-span-padding) 0;
    }

    .jp-RenderedText pre .ansi-blue-intense-bg {
    background-color: #0065ca;
    padding: var(--jp-private-code-span-padding) 0;
    }

    .jp-RenderedText pre .ansi-magenta-intense-bg {
    background-color: #a03196;
    padding: var(--jp-private-code-span-padding) 0;
    }

    .jp-RenderedText pre .ansi-cyan-intense-bg {
    background-color: #258f8f;
    padding: var(--jp-private-code-span-padding) 0;
    }

    .jp-RenderedText pre .ansi-white-intense-bg {
    background-color: #a1a6b2;
    padding: var(--jp-private-code-span-padding) 0;
    }

    .jp-RenderedText pre .ansi-default-inverse-fg {
    color: var(--jp-ui-inverse-font-color0);
    }

    .jp-RenderedText pre .ansi-default-inverse-bg {
    background-color: var(--jp-inverse-layout-color0);
    padding: var(--jp-private-code-span-padding) 0;
    }

    .jp-RenderedText pre .ansi-bold {
    font-weight: bold;
    }

    .jp-RenderedText pre .ansi-underline {
    text-decoration: underline;
    }

    .jp-RenderedText[data-mime-type='application/vnd.jupyter.stderr'] {
    background: var(--jp-rendermime-error-background);
    padding-top: var(--jp-code-padding);
    }

    /*-----------------------------------------------------------------------------
    | RenderedLatex
    |----------------------------------------------------------------------------*/

    .jp-RenderedLatex {
    color: var(--jp-content-font-color1);
    font-size: var(--jp-content-font-size1);
    line-height: var(--jp-content-line-height);
    }

    /* Left-justify outputs.*/
    .jp-OutputArea-output.jp-RenderedLatex {
    padding: var(--jp-code-padding);
    text-align: left;
    }

    /*-----------------------------------------------------------------------------
    | RenderedHTML
    |----------------------------------------------------------------------------*/

    .jp-RenderedHTMLCommon {
    color: var(--jp-content-font-color1);
    font-family: var(--jp-content-font-family);
    font-size: var(--jp-content-font-size1);
    line-height: var(--jp-content-line-height);

    /* Give a bit more R padding on Markdown text to keep line lengths reasonable */
    padding-right: 20px;
    }

    .jp-RenderedHTMLCommon em {
    font-style: italic;
    }

    .jp-RenderedHTMLCommon strong {
    font-weight: bold;
    }

    .jp-RenderedHTMLCommon u {
    text-decoration: underline;
    }

    .jp-RenderedHTMLCommon a:link {
    text-decoration: none;
    color: var(--jp-content-link-color);
    }

    .jp-RenderedHTMLCommon a:hover {
    text-decoration: underline;
    color: var(--jp-content-link-color);
    }

    .jp-RenderedHTMLCommon a:visited {
    text-decoration: none;
    color: var(--jp-content-link-color);
    }

    /* Headings */

    .jp-RenderedHTMLCommon h1,
    .jp-RenderedHTMLCommon h2,
    .jp-RenderedHTMLCommon h3,
    .jp-RenderedHTMLCommon h4,
    .jp-RenderedHTMLCommon h5,
    .jp-RenderedHTMLCommon h6 {
    line-height: var(--jp-content-heading-line-height);
    font-weight: var(--jp-content-heading-font-weight);
    font-style: normal;
    margin: var(--jp-content-heading-margin-top) 0
        var(--jp-content-heading-margin-bottom) 0;
    }

    .jp-RenderedHTMLCommon h1:first-child,
    .jp-RenderedHTMLCommon h2:first-child,
    .jp-RenderedHTMLCommon h3:first-child,
    .jp-RenderedHTMLCommon h4:first-child,
    .jp-RenderedHTMLCommon h5:first-child,
    .jp-RenderedHTMLCommon h6:first-child {
    margin-top: calc(0.5 * var(--jp-content-heading-margin-top));
    }

    .jp-RenderedHTMLCommon h1:last-child,
    .jp-RenderedHTMLCommon h2:last-child,
    .jp-RenderedHTMLCommon h3:last-child,
    .jp-RenderedHTMLCommon h4:last-child,
    .jp-RenderedHTMLCommon h5:last-child,
    .jp-RenderedHTMLCommon h6:last-child {
    margin-bottom: calc(0.5 * var(--jp-content-heading-margin-bottom));
    }

    .jp-RenderedHTMLCommon h1 {
    font-size: var(--jp-content-font-size5);
    }

    .jp-RenderedHTMLCommon h2 {
    font-size: var(--jp-content-font-size4);
    }

    .jp-RenderedHTMLCommon h3 {
    font-size: var(--jp-content-font-size3);
    }

    .jp-RenderedHTMLCommon h4 {
    font-size: var(--jp-content-font-size2);
    }

    .jp-RenderedHTMLCommon h5 {
    font-size: var(--jp-content-font-size1);
    }

    .jp-RenderedHTMLCommon h6 {
    font-size: var(--jp-content-font-size0);
    }

    /* Lists */

    /* stylelint-disable selector-max-type, selector-max-compound-selectors */

    .jp-RenderedHTMLCommon ul:not(.list-inline),
    .jp-RenderedHTMLCommon ol:not(.list-inline) {
    padding-left: 2em;
    }

    .jp-RenderedHTMLCommon ul {
    list-style: disc;
    }

    .jp-RenderedHTMLCommon ul ul {
    list-style: square;
    }

    .jp-RenderedHTMLCommon ul ul ul {
    list-style: circle;
    }

    .jp-RenderedHTMLCommon ol {
    list-style: decimal;
    }

    .jp-RenderedHTMLCommon ol ol {
    list-style: upper-alpha;
    }

    .jp-RenderedHTMLCommon ol ol ol {
    list-style: lower-alpha;
    }

    .jp-RenderedHTMLCommon ol ol ol ol {
    list-style: lower-roman;
    }

    .jp-RenderedHTMLCommon ol ol ol ol ol {
    list-style: decimal;
    }

    .jp-RenderedHTMLCommon ol,
    .jp-RenderedHTMLCommon ul {
    margin-bottom: 1em;
    }

    .jp-RenderedHTMLCommon ul ul,
    .jp-RenderedHTMLCommon ul ol,
    .jp-RenderedHTMLCommon ol ul,
    .jp-RenderedHTMLCommon ol ol {
    margin-bottom: 0;
    }

    /* stylelint-enable selector-max-type, selector-max-compound-selectors */

    .jp-RenderedHTMLCommon hr {
    color: var(--jp-border-color2);
    background-color: var(--jp-border-color1);
    margin-top: 1em;
    margin-bottom: 1em;
    }

    .jp-RenderedHTMLCommon > pre {
    margin: 1.5em 2em;
    }

    .jp-RenderedHTMLCommon pre,
    .jp-RenderedHTMLCommon code {
    border: 0;
    background-color: var(--jp-layout-color0);
    color: var(--jp-content-font-color1);
    font-family: var(--jp-code-font-family);
    font-size: inherit;
    line-height: var(--jp-code-line-height);
    padding: 0;
    white-space: pre-wrap;
    }

    .jp-RenderedHTMLCommon :not(pre) > code {
    background-color: var(--jp-layout-color2);
    padding: 1px 5px;
    }

    /* Tables */

    .jp-RenderedHTMLCommon table {
    border-collapse: collapse;
    border-spacing: 0;
    border: none;
    color: var(--jp-ui-font-color1);
    font-size: var(--jp-ui-font-size1);
    table-layout: fixed;
    margin-left: auto;
    margin-bottom: 1em;
    margin-right: auto;
    }

    .jp-RenderedHTMLCommon thead {
    border-bottom: var(--jp-border-width) solid var(--jp-border-color1);
    vertical-align: bottom;
    }

    .jp-RenderedHTMLCommon td,
    .jp-RenderedHTMLCommon th,
    .jp-RenderedHTMLCommon tr {
    vertical-align: middle;
    padding: 0.5em;
    line-height: normal;
    white-space: normal;
    max-width: none;
    border: none;
    }

    .jp-RenderedMarkdown.jp-RenderedHTMLCommon td,
    .jp-RenderedMarkdown.jp-RenderedHTMLCommon th {
    max-width: none;
    }

    :not(.jp-RenderedMarkdown).jp-RenderedHTMLCommon td,
    :not(.jp-RenderedMarkdown).jp-RenderedHTMLCommon th,
    :not(.jp-RenderedMarkdown).jp-RenderedHTMLCommon tr {
    text-align: right;
    }

    .jp-RenderedHTMLCommon th {
    font-weight: bold;
    }

    .jp-RenderedHTMLCommon tbody tr:nth-child(odd) {
    background: var(--jp-layout-color0);
    }

    .jp-RenderedHTMLCommon tbody tr:nth-child(even) {
    background: var(--jp-rendermime-table-row-background);
    }

    .jp-RenderedHTMLCommon tbody tr:hover {
    background: var(--jp-rendermime-table-row-hover-background);
    }

    .jp-RenderedHTMLCommon p {
    text-align: left;
    margin: 0;
    margin-bottom: 1em;
    }

    .jp-RenderedHTMLCommon img {
    -moz-force-broken-image-icon: 1;
    }

    /* Restrict to direct children as other images could be nested in other content. */
    .jp-RenderedHTMLCommon > img {
    display: block;
    margin-left: 0;
    margin-right: 0;
    margin-bottom: 1em;
    }

    /* Change color behind transparent images if they need it... */
    [data-jp-theme-light='false'] .jp-RenderedImage img.jp-needs-light-background {
    background-color: var(--jp-inverse-layout-color1);
    }

    [data-jp-theme-light='true'] .jp-RenderedImage img.jp-needs-dark-background {
    background-color: var(--jp-inverse-layout-color1);
    }

    .jp-RenderedHTMLCommon img,
    .jp-RenderedImage img,
    .jp-RenderedHTMLCommon svg,
    .jp-RenderedSVG svg {
    max-width: 100%;
    height: auto;
    }

    .jp-RenderedHTMLCommon img.jp-mod-unconfined,
    .jp-RenderedImage img.jp-mod-unconfined,
    .jp-RenderedHTMLCommon svg.jp-mod-unconfined,
    .jp-RenderedSVG svg.jp-mod-unconfined {
    max-width: none;
    }

    .jp-RenderedHTMLCommon .alert {
    padding: var(--jp-notebook-padding);
    border: var(--jp-border-width) solid transparent;
    border-radius: var(--jp-border-radius);
    margin-bottom: 1em;
    }

    .jp-RenderedHTMLCommon .alert-info {
    color: var(--jp-info-color0);
    background-color: var(--jp-info-color3);
    border-color: var(--jp-info-color2);
    }

    .jp-RenderedHTMLCommon .alert-info hr {
    border-color: var(--jp-info-color3);
    }

    .jp-RenderedHTMLCommon .alert-info > p:last-child,
    .jp-RenderedHTMLCommon .alert-info > ul:last-child {
    margin-bottom: 0;
    }

    .jp-RenderedHTMLCommon .alert-warning {
    color: var(--jp-warn-color0);
    background-color: var(--jp-warn-color3);
    border-color: var(--jp-warn-color2);
    }

    .jp-RenderedHTMLCommon .alert-warning hr {
    border-color: var(--jp-warn-color3);
    }

    .jp-RenderedHTMLCommon .alert-warning > p:last-child,
    .jp-RenderedHTMLCommon .alert-warning > ul:last-child {
    margin-bottom: 0;
    }

    .jp-RenderedHTMLCommon .alert-success {
    color: var(--jp-success-color0);
    background-color: var(--jp-success-color3);
    border-color: var(--jp-success-color2);
    }

    .jp-RenderedHTMLCommon .alert-success hr {
    border-color: var(--jp-success-color3);
    }

    .jp-RenderedHTMLCommon .alert-success > p:last-child,
    .jp-RenderedHTMLCommon .alert-success > ul:last-child {
    margin-bottom: 0;
    }

    .jp-RenderedHTMLCommon .alert-danger {
    color: var(--jp-error-color0);
    background-color: var(--jp-error-color3);
    border-color: var(--jp-error-color2);
    }

    .jp-RenderedHTMLCommon .alert-danger hr {
    border-color: var(--jp-error-color3);
    }

    .jp-RenderedHTMLCommon .alert-danger > p:last-child,
    .jp-RenderedHTMLCommon .alert-danger > ul:last-child {
    margin-bottom: 0;
    }

    .jp-RenderedHTMLCommon blockquote {
    margin: 1em 2em;
    padding: 0 1em;
    border-left: 5px solid var(--jp-border-color2);
    }

    a.jp-InternalAnchorLink {
    visibility: hidden;
    margin-left: 8px;
    color: var(--md-blue-800);
    }

    h1:hover .jp-InternalAnchorLink,
    h2:hover .jp-InternalAnchorLink,
    h3:hover .jp-InternalAnchorLink,
    h4:hover .jp-InternalAnchorLink,
    h5:hover .jp-InternalAnchorLink,
    h6:hover .jp-InternalAnchorLink {
    visibility: visible;
    }

    .jp-RenderedHTMLCommon kbd {
    background-color: var(--jp-rendermime-table-row-background);
    border: 1px solid var(--jp-border-color0);
    border-bottom-color: var(--jp-border-color2);
    border-radius: 3px;
    box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.25);
    display: inline-block;
    font-size: var(--jp-ui-font-size0);
    line-height: 1em;
    padding: 0.2em 0.5em;
    }

    /* Most direct children of .jp-RenderedHTMLCommon have a margin-bottom of 1.0.
    * At the bottom of cells this is a bit too much as there is also spacing
    * between cells. Going all the way to 0 gets too tight between markdown and
    * code cells.
    */
    .jp-RenderedHTMLCommon > *:last-child {
    margin-bottom: 0.5em;
    }

    /*
    * Copyright (c) Jupyter Development Team.
    * Distributed under the terms of the Modified BSD License.
    */

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Copyright (c) 2014-2017, PhosphorJS Contributors
    |
    | Distributed under the terms of the BSD 3-Clause License.
    |
    | The full license is in the file LICENSE, distributed with this software.
    |----------------------------------------------------------------------------*/

    .lm-cursor-backdrop {
    position: fixed;
    width: 200px;
    height: 200px;
    margin-top: -100px;
    margin-left: -100px;
    will-change: transform;
    z-index: 100;
    }

    .lm-mod-drag-image {
    will-change: transform;
    }

    /*
    * Copyright (c) Jupyter Development Team.
    * Distributed under the terms of the Modified BSD License.
    */

    .jp-lineFormSearch {
    padding: 4px 12px;
    background-color: var(--jp-layout-color2);
    box-shadow: var(--jp-toolbar-box-shadow);
    z-index: 2;
    font-size: var(--jp-ui-font-size1);
    }

    .jp-lineFormCaption {
    font-size: var(--jp-ui-font-size0);
    line-height: var(--jp-ui-font-size1);
    margin-top: 4px;
    color: var(--jp-ui-font-color0);
    }

    .jp-baseLineForm {
    border: none;
    border-radius: 0;
    position: absolute;
    background-size: 16px;
    background-repeat: no-repeat;
    background-position: center;
    outline: none;
    }

    .jp-lineFormButtonContainer {
    top: 4px;
    right: 8px;
    height: 24px;
    padding: 0 12px;
    width: 12px;
    }

    .jp-lineFormButtonIcon {
    top: 0;
    right: 0;
    background-color: var(--jp-brand-color1);
    height: 100%;
    width: 100%;
    box-sizing: border-box;
    padding: 4px 6px;
    }

    .jp-lineFormButton {
    top: 0;
    right: 0;
    background-color: transparent;
    height: 100%;
    width: 100%;
    box-sizing: border-box;
    }

    .jp-lineFormWrapper {
    overflow: hidden;
    padding: 0 8px;
    border: 1px solid var(--jp-border-color0);
    background-color: var(--jp-input-active-background);
    height: 22px;
    }

    .jp-lineFormWrapperFocusWithin {
    border: var(--jp-border-width) solid var(--md-blue-500);
    box-shadow: inset 0 0 4px var(--md-blue-300);
    }

    .jp-lineFormInput {
    background: transparent;
    width: 200px;
    height: 100%;
    border: none;
    outline: none;
    color: var(--jp-ui-font-color0);
    line-height: 28px;
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) 2014-2016, Jupyter Development Team.
    |
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    .jp-JSONEditor {
    display: flex;
    flex-direction: column;
    width: 100%;
    }

    .jp-JSONEditor-host {
    flex: 1 1 auto;
    border: var(--jp-border-width) solid var(--jp-input-border-color);
    border-radius: 0;
    background: var(--jp-layout-color0);
    min-height: 50px;
    padding: 1px;
    }

    .jp-JSONEditor.jp-mod-error .jp-JSONEditor-host {
    border-color: red;
    outline-color: red;
    }

    .jp-JSONEditor-header {
    display: flex;
    flex: 1 0 auto;
    padding: 0 0 0 12px;
    }

    .jp-JSONEditor-header label {
    flex: 0 0 auto;
    }

    .jp-JSONEditor-commitButton {
    height: 16px;
    width: 16px;
    background-size: 18px;
    background-repeat: no-repeat;
    background-position: center;
    }

    .jp-JSONEditor-host.jp-mod-focused {
    background-color: var(--jp-input-active-background);
    border: 1px solid var(--jp-input-active-border-color);
    box-shadow: var(--jp-input-box-shadow);
    }

    .jp-Editor.jp-mod-dropTarget {
    border: var(--jp-border-width) solid var(--jp-input-active-border-color);
    box-shadow: var(--jp-input-box-shadow);
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/
    .jp-DocumentSearch-input {
    border: none;
    outline: none;
    color: var(--jp-ui-font-color0);
    font-size: var(--jp-ui-font-size1);
    background-color: var(--jp-layout-color0);
    font-family: var(--jp-ui-font-family);
    padding: 2px 1px;
    resize: none;
    }

    .jp-DocumentSearch-overlay {
    position: absolute;
    background-color: var(--jp-toolbar-background);
    border-bottom: var(--jp-border-width) solid var(--jp-toolbar-border-color);
    border-left: var(--jp-border-width) solid var(--jp-toolbar-border-color);
    top: 0;
    right: 0;
    z-index: 7;
    min-width: 405px;
    padding: 2px;
    font-size: var(--jp-ui-font-size1);

    --jp-private-document-search-button-height: 20px;
    }

    .jp-DocumentSearch-overlay button {
    background-color: var(--jp-toolbar-background);
    outline: 0;
    }

    .jp-DocumentSearch-overlay button:hover {
    background-color: var(--jp-layout-color2);
    }

    .jp-DocumentSearch-overlay button:active {
    background-color: var(--jp-layout-color3);
    }

    .jp-DocumentSearch-overlay-row {
    display: flex;
    align-items: center;
    margin-bottom: 2px;
    }

    .jp-DocumentSearch-button-content {
    display: inline-block;
    cursor: pointer;
    box-sizing: border-box;
    width: 100%;
    height: 100%;
    }

    .jp-DocumentSearch-button-content svg {
    width: 100%;
    height: 100%;
    }

    .jp-DocumentSearch-input-wrapper {
    border: var(--jp-border-width) solid var(--jp-border-color0);
    display: flex;
    background-color: var(--jp-layout-color0);
    margin: 2px;
    }

    .jp-DocumentSearch-input-wrapper:focus-within {
    border-color: var(--jp-cell-editor-active-border-color);
    }

    .jp-DocumentSearch-toggle-wrapper,
    .jp-DocumentSearch-button-wrapper {
    all: initial;
    overflow: hidden;
    display: inline-block;
    border: none;
    box-sizing: border-box;
    }

    .jp-DocumentSearch-toggle-wrapper {
    width: 14px;
    height: 14px;
    }

    .jp-DocumentSearch-button-wrapper {
    width: var(--jp-private-document-search-button-height);
    height: var(--jp-private-document-search-button-height);
    }

    .jp-DocumentSearch-toggle-wrapper:focus,
    .jp-DocumentSearch-button-wrapper:focus {
    outline: var(--jp-border-width) solid
        var(--jp-cell-editor-active-border-color);
    outline-offset: -1px;
    }

    .jp-DocumentSearch-toggle-wrapper,
    .jp-DocumentSearch-button-wrapper,
    .jp-DocumentSearch-button-content:focus {
    outline: none;
    }

    .jp-DocumentSearch-toggle-placeholder {
    width: 5px;
    }

    .jp-DocumentSearch-input-button::before {
    display: block;
    padding-top: 100%;
    }

    .jp-DocumentSearch-input-button-off {
    opacity: var(--jp-search-toggle-off-opacity);
    }

    .jp-DocumentSearch-input-button-off:hover {
    opacity: var(--jp-search-toggle-hover-opacity);
    }

    .jp-DocumentSearch-input-button-on {
    opacity: var(--jp-search-toggle-on-opacity);
    }

    .jp-DocumentSearch-index-counter {
    padding-left: 10px;
    padding-right: 10px;
    user-select: none;
    min-width: 35px;
    display: inline-block;
    }

    .jp-DocumentSearch-up-down-wrapper {
    display: inline-block;
    padding-right: 2px;
    margin-left: auto;
    white-space: nowrap;
    }

    .jp-DocumentSearch-spacer {
    margin-left: auto;
    }

    .jp-DocumentSearch-up-down-wrapper button {
    outline: 0;
    border: none;
    width: var(--jp-private-document-search-button-height);
    height: var(--jp-private-document-search-button-height);
    vertical-align: middle;
    margin: 1px 5px 2px;
    }

    .jp-DocumentSearch-up-down-button:hover {
    background-color: var(--jp-layout-color2);
    }

    .jp-DocumentSearch-up-down-button:active {
    background-color: var(--jp-layout-color3);
    }

    .jp-DocumentSearch-filter-button {
    border-radius: var(--jp-border-radius);
    }

    .jp-DocumentSearch-filter-button:hover {
    background-color: var(--jp-layout-color2);
    }

    .jp-DocumentSearch-filter-button-enabled {
    background-color: var(--jp-layout-color2);
    }

    .jp-DocumentSearch-filter-button-enabled:hover {
    background-color: var(--jp-layout-color3);
    }

    .jp-DocumentSearch-search-options {
    padding: 0 8px;
    margin-left: 3px;
    width: 100%;
    display: grid;
    justify-content: start;
    grid-template-columns: 1fr 1fr;
    align-items: center;
    justify-items: stretch;
    }

    .jp-DocumentSearch-search-filter-disabled {
    color: var(--jp-ui-font-color2);
    }

    .jp-DocumentSearch-search-filter {
    display: flex;
    align-items: center;
    user-select: none;
    }

    .jp-DocumentSearch-regex-error {
    color: var(--jp-error-color0);
    }

    .jp-DocumentSearch-replace-button-wrapper {
    overflow: hidden;
    display: inline-block;
    box-sizing: border-box;
    border: var(--jp-border-width) solid var(--jp-border-color0);
    margin: auto 2px;
    padding: 1px 4px;
    height: calc(var(--jp-private-document-search-button-height) + 2px);
    }

    .jp-DocumentSearch-replace-button-wrapper:focus {
    border: var(--jp-border-width) solid var(--jp-cell-editor-active-border-color);
    }

    .jp-DocumentSearch-replace-button {
    display: inline-block;
    text-align: center;
    cursor: pointer;
    box-sizing: border-box;
    color: var(--jp-ui-font-color1);

    /* height - 2 * (padding of wrapper) */
    line-height: calc(var(--jp-private-document-search-button-height) - 2px);
    width: 100%;
    height: 100%;
    }

    .jp-DocumentSearch-replace-button:focus {
    outline: none;
    }

    .jp-DocumentSearch-replace-wrapper-class {
    margin-left: 14px;
    display: flex;
    }

    .jp-DocumentSearch-replace-toggle {
    border: none;
    background-color: var(--jp-toolbar-background);
    border-radius: var(--jp-border-radius);
    }

    .jp-DocumentSearch-replace-toggle:hover {
    background-color: var(--jp-layout-color2);
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    .cm-editor {
    line-height: var(--jp-code-line-height);
    font-size: var(--jp-code-font-size);
    font-family: var(--jp-code-font-family);
    border: 0;
    border-radius: 0;
    height: auto;

    /* Changed to auto to autogrow */
    }

    .cm-editor pre {
    padding: 0 var(--jp-code-padding);
    }

    .jp-CodeMirrorEditor[data-type='inline'] .cm-dialog {
    background-color: var(--jp-layout-color0);
    color: var(--jp-content-font-color1);
    }

    .jp-CodeMirrorEditor {
    cursor: text;
    }

    /* When zoomed out 67% and 33% on a screen of 1440 width x 900 height */
    @media screen and (min-width: 2138px) and (max-width: 4319px) {
    .jp-CodeMirrorEditor[data-type='inline'] .cm-cursor {
        border-left: var(--jp-code-cursor-width1) solid
        var(--jp-editor-cursor-color);
    }
    }

    /* When zoomed out less than 33% */
    @media screen and (min-width: 4320px) {
    .jp-CodeMirrorEditor[data-type='inline'] .cm-cursor {
        border-left: var(--jp-code-cursor-width2) solid
        var(--jp-editor-cursor-color);
    }
    }

    .cm-editor.jp-mod-readOnly .cm-cursor {
    display: none;
    }

    .jp-CollaboratorCursor {
    border-left: 5px solid transparent;
    border-right: 5px solid transparent;
    border-top: none;
    border-bottom: 3px solid;
    background-clip: content-box;
    margin-left: -5px;
    margin-right: -5px;
    }

    .cm-searching,
    .cm-searching span {
    /* `.cm-searching span`: we need to override syntax highlighting */
    background-color: var(--jp-search-unselected-match-background-color);
    color: var(--jp-search-unselected-match-color);
    }

    .cm-searching::selection,
    .cm-searching span::selection {
    background-color: var(--jp-search-unselected-match-background-color);
    color: var(--jp-search-unselected-match-color);
    }

    .jp-current-match > .cm-searching,
    .jp-current-match > .cm-searching span,
    .cm-searching > .jp-current-match,
    .cm-searching > .jp-current-match span {
    background-color: var(--jp-search-selected-match-background-color);
    color: var(--jp-search-selected-match-color);
    }

    .jp-current-match > .cm-searching::selection,
    .cm-searching > .jp-current-match::selection,
    .jp-current-match > .cm-searching span::selection {
    background-color: var(--jp-search-selected-match-background-color);
    color: var(--jp-search-selected-match-color);
    }

    .cm-trailingspace {
    background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAgAAAAFCAYAAAB4ka1VAAAAsElEQVQIHQGlAFr/AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA7+r3zKmT0/+pk9P/7+r3zAAAAAAAAAAABAAAAAAAAAAA6OPzM+/q9wAAAAAA6OPzMwAAAAAAAAAAAgAAAAAAAAAAGR8NiRQaCgAZIA0AGR8NiQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAQyoYJ/SY80UAAAAASUVORK5CYII=);
    background-position: center left;
    background-repeat: repeat-x;
    }

    .jp-CollaboratorCursor-hover {
    position: absolute;
    z-index: 1;
    transform: translateX(-50%);
    color: white;
    border-radius: 3px;
    padding-left: 4px;
    padding-right: 4px;
    padding-top: 1px;
    padding-bottom: 1px;
    text-align: center;
    font-size: var(--jp-ui-font-size1);
    white-space: nowrap;
    }

    .jp-CodeMirror-ruler {
    border-left: 1px dashed var(--jp-border-color2);
    }

    /* Styles for shared cursors (remote cursor locations and selected ranges) */
    .jp-CodeMirrorEditor .cm-ySelectionCaret {
    position: relative;
    border-left: 1px solid black;
    margin-left: -1px;
    margin-right: -1px;
    box-sizing: border-box;
    }

    .jp-CodeMirrorEditor .cm-ySelectionCaret > .cm-ySelectionInfo {
    white-space: nowrap;
    position: absolute;
    top: -1.15em;
    padding-bottom: 0.05em;
    left: -1px;
    font-size: 0.95em;
    font-family: var(--jp-ui-font-family);
    font-weight: bold;
    line-height: normal;
    user-select: none;
    color: white;
    padding-left: 2px;
    padding-right: 2px;
    z-index: 101;
    transition: opacity 0.3s ease-in-out;
    }

    .jp-CodeMirrorEditor .cm-ySelectionInfo {
    transition-delay: 0.7s;
    opacity: 0;
    }

    .jp-CodeMirrorEditor .cm-ySelectionCaret:hover > .cm-ySelectionInfo {
    opacity: 1;
    transition-delay: 0s;
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    .jp-MimeDocument {
    outline: none;
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    /*-----------------------------------------------------------------------------
    | Variables
    |----------------------------------------------------------------------------*/

    :root {
    --jp-private-filebrowser-button-height: 28px;
    --jp-private-filebrowser-button-width: 48px;
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    .jp-FileBrowser .jp-SidePanel-content {
    display: flex;
    flex-direction: column;
    }

    .jp-FileBrowser-toolbar.jp-Toolbar {
    flex-wrap: wrap;
    row-gap: 12px;
    border-bottom: none;
    height: auto;
    margin: 8px 12px 0;
    box-shadow: none;
    padding: 0;
    justify-content: flex-start;
    }

    .jp-FileBrowser-Panel {
    flex: 1 1 auto;
    display: flex;
    flex-direction: column;
    }

    .jp-BreadCrumbs {
    flex: 0 0 auto;
    margin: 8px 12px;
    }

    .jp-BreadCrumbs-item {
    margin: 0 2px;
    padding: 0 2px;
    border-radius: var(--jp-border-radius);
    cursor: pointer;
    }

    .jp-BreadCrumbs-item:hover {
    background-color: var(--jp-layout-color2);
    }

    .jp-BreadCrumbs-item:first-child {
    margin-left: 0;
    }

    .jp-BreadCrumbs-item.jp-mod-dropTarget {
    background-color: var(--jp-brand-color2);
    opacity: 0.7;
    }

    /*-----------------------------------------------------------------------------
    | Buttons
    |----------------------------------------------------------------------------*/

    .jp-FileBrowser-toolbar > .jp-Toolbar-item {
    flex: 0 0 auto;
    padding-left: 0;
    padding-right: 2px;
    align-items: center;
    height: unset;
    }

    .jp-FileBrowser-toolbar > .jp-Toolbar-item .jp-ToolbarButtonComponent {
    width: 40px;
    }

    /*-----------------------------------------------------------------------------
    | Other styles
    |----------------------------------------------------------------------------*/

    .jp-FileDialog.jp-mod-conflict input {
    color: var(--jp-error-color1);
    }

    .jp-FileDialog .jp-new-name-title {
    margin-top: 12px;
    }

    .jp-LastModified-hidden {
    display: none;
    }

    .jp-FileSize-hidden {
    display: none;
    }

    .jp-FileBrowser .lm-AccordionPanel > h3:first-child {
    display: none;
    }

    /*-----------------------------------------------------------------------------
    | DirListing
    |----------------------------------------------------------------------------*/

    .jp-DirListing {
    flex: 1 1 auto;
    display: flex;
    flex-direction: column;
    outline: 0;
    }

    .jp-DirListing-header {
    flex: 0 0 auto;
    display: flex;
    flex-direction: row;
    align-items: center;
    overflow: hidden;
    border-top: var(--jp-border-width) solid var(--jp-border-color2);
    border-bottom: var(--jp-border-width) solid var(--jp-border-color1);
    box-shadow: var(--jp-toolbar-box-shadow);
    z-index: 2;
    }

    .jp-DirListing-headerItem {
    padding: 4px 12px 2px;
    font-weight: 500;
    }

    .jp-DirListing-headerItem:hover {
    background: var(--jp-layout-color2);
    }

    .jp-DirListing-headerItem.jp-id-name {
    flex: 1 0 84px;
    }

    .jp-DirListing-headerItem.jp-id-modified {
    flex: 0 0 112px;
    border-left: var(--jp-border-width) solid var(--jp-border-color2);
    text-align: right;
    }

    .jp-DirListing-headerItem.jp-id-filesize {
    flex: 0 0 75px;
    border-left: var(--jp-border-width) solid var(--jp-border-color2);
    text-align: right;
    }

    .jp-id-narrow {
    display: none;
    flex: 0 0 5px;
    padding: 4px;
    border-left: var(--jp-border-width) solid var(--jp-border-color2);
    text-align: right;
    color: var(--jp-border-color2);
    }

    .jp-DirListing-narrow .jp-id-narrow {
    display: block;
    }

    .jp-DirListing-narrow .jp-id-modified,
    .jp-DirListing-narrow .jp-DirListing-itemModified {
    display: none;
    }

    .jp-DirListing-headerItem.jp-mod-selected {
    font-weight: 600;
    }

    /* increase specificity to override bundled default */
    .jp-DirListing-content {
    flex: 1 1 auto;
    margin: 0;
    padding: 0;
    list-style-type: none;
    overflow: auto;
    background-color: var(--jp-layout-color1);
    }

    .jp-DirListing-content mark {
    color: var(--jp-ui-font-color0);
    background-color: transparent;
    font-weight: bold;
    }

    .jp-DirListing-content .jp-DirListing-item.jp-mod-selected mark {
    color: var(--jp-ui-inverse-font-color0);
    }

    /* Style the directory listing content when a user drops a file to upload */
    .jp-DirListing.jp-mod-native-drop .jp-DirListing-content {
    outline: 5px dashed rgba(128, 128, 128, 0.5);
    outline-offset: -10px;
    cursor: copy;
    }

    .jp-DirListing-item {
    display: flex;
    flex-direction: row;
    align-items: center;
    padding: 4px 12px;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    }

    .jp-DirListing-checkboxWrapper {
    /* Increases hit area of checkbox. */
    padding: 4px;
    }

    .jp-DirListing-header
    .jp-DirListing-checkboxWrapper
    + .jp-DirListing-headerItem {
    padding-left: 4px;
    }

    .jp-DirListing-content .jp-DirListing-checkboxWrapper {
    position: relative;
    left: -4px;
    margin: -4px 0 -4px -8px;
    }

    .jp-DirListing-checkboxWrapper.jp-mod-visible {
    visibility: visible;
    }

    /* For devices that support hovering, hide checkboxes until hovered, selected...
    */
    @media (hover: hover) {
    .jp-DirListing-checkboxWrapper {
        visibility: hidden;
    }

    .jp-DirListing-item:hover .jp-DirListing-checkboxWrapper,
    .jp-DirListing-item.jp-mod-selected .jp-DirListing-checkboxWrapper {
        visibility: visible;
    }
    }

    .jp-DirListing-item[data-is-dot] {
    opacity: 75%;
    }

    .jp-DirListing-item.jp-mod-selected {
    color: var(--jp-ui-inverse-font-color1);
    background: var(--jp-brand-color1);
    }

    .jp-DirListing-item.jp-mod-dropTarget {
    background: var(--jp-brand-color3);
    }

    .jp-DirListing-item:hover:not(.jp-mod-selected) {
    background: var(--jp-layout-color2);
    }

    .jp-DirListing-itemIcon {
    flex: 0 0 20px;
    margin-right: 4px;
    }

    .jp-DirListing-itemText {
    flex: 1 0 64px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    user-select: none;
    }

    .jp-DirListing-itemText:focus {
    outline-width: 2px;
    outline-color: var(--jp-inverse-layout-color1);
    outline-style: solid;
    outline-offset: 1px;
    }

    .jp-DirListing-item.jp-mod-selected .jp-DirListing-itemText:focus {
    outline-color: var(--jp-layout-color1);
    }

    .jp-DirListing-itemModified {
    flex: 0 0 125px;
    text-align: right;
    }

    .jp-DirListing-itemFileSize {
    flex: 0 0 90px;
    text-align: right;
    }

    .jp-DirListing-editor {
    flex: 1 0 64px;
    outline: none;
    border: none;
    color: var(--jp-ui-font-color1);
    background-color: var(--jp-layout-color1);
    }

    .jp-DirListing-item.jp-mod-running .jp-DirListing-itemIcon::before {
    color: var(--jp-success-color1);
    content: '\25CF';
    font-size: 8px;
    position: absolute;
    left: -8px;
    }

    .jp-DirListing-item.jp-mod-running.jp-mod-selected
    .jp-DirListing-itemIcon::before {
    color: var(--jp-ui-inverse-font-color1);
    }

    .jp-DirListing-item.lm-mod-drag-image,
    .jp-DirListing-item.jp-mod-selected.lm-mod-drag-image {
    font-size: var(--jp-ui-font-size1);
    padding-left: 4px;
    margin-left: 4px;
    width: 160px;
    background-color: var(--jp-ui-inverse-font-color2);
    box-shadow: var(--jp-elevation-z2);
    border-radius: 0;
    color: var(--jp-ui-font-color1);
    transform: translateX(-40%) translateY(-58%);
    }

    .jp-Document {
    min-width: 120px;
    min-height: 120px;
    outline: none;
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    /*-----------------------------------------------------------------------------
    | Main OutputArea
    | OutputArea has a list of Outputs
    |----------------------------------------------------------------------------*/

    .jp-OutputArea {
    overflow-y: auto;
    }

    .jp-OutputArea-child {
    display: table;
    table-layout: fixed;
    width: 100%;
    overflow: hidden;
    }

    .jp-OutputPrompt {
    width: var(--jp-cell-prompt-width);
    color: var(--jp-cell-outprompt-font-color);
    font-family: var(--jp-cell-prompt-font-family);
    padding: var(--jp-code-padding);
    letter-spacing: var(--jp-cell-prompt-letter-spacing);
    line-height: var(--jp-code-line-height);
    font-size: var(--jp-code-font-size);
    border: var(--jp-border-width) solid transparent;
    opacity: var(--jp-cell-prompt-opacity);

    /* Right align prompt text, don't wrap to handle large prompt numbers */
    text-align: right;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;

    /* Disable text selection */
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    }

    .jp-OutputArea-prompt {
    display: table-cell;
    vertical-align: top;
    }

    .jp-OutputArea-output {
    display: table-cell;
    width: 100%;
    height: auto;
    overflow: auto;
    user-select: text;
    -moz-user-select: text;
    -webkit-user-select: text;
    -ms-user-select: text;
    }

    .jp-OutputArea .jp-RenderedText {
    padding-left: 1ch;
    }

    /**
    * Prompt overlay.
    */

    .jp-OutputArea-promptOverlay {
    position: absolute;
    top: 0;
    width: var(--jp-cell-prompt-width);
    height: 100%;
    opacity: 0.5;
    }

    .jp-OutputArea-promptOverlay:hover {
    background: var(--jp-layout-color2);
    box-shadow: inset 0 0 1px var(--jp-inverse-layout-color0);
    cursor: zoom-out;
    }

    .jp-mod-outputsScrolled .jp-OutputArea-promptOverlay:hover {
    cursor: zoom-in;
    }

    /**
    * Isolated output.
    */
    .jp-OutputArea-output.jp-mod-isolated {
    width: 100%;
    display: block;
    }

    /*
    When drag events occur, `lm-mod-override-cursor` is added to the body.
    Because iframes steal all cursor events, the following two rules are necessary
    to suppress pointer events while resize drags are occurring. There may be a
    better solution to this problem.
    */
    body.lm-mod-override-cursor .jp-OutputArea-output.jp-mod-isolated {
    position: relative;
    }

    body.lm-mod-override-cursor .jp-OutputArea-output.jp-mod-isolated::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: transparent;
    }

    /* pre */

    .jp-OutputArea-output pre {
    border: none;
    margin: 0;
    padding: 0;
    overflow-x: auto;
    overflow-y: auto;
    word-break: break-all;
    word-wrap: break-word;
    white-space: pre-wrap;
    }

    /* tables */

    .jp-OutputArea-output.jp-RenderedHTMLCommon table {
    margin-left: 0;
    margin-right: 0;
    }

    /* description lists */

    .jp-OutputArea-output dl,
    .jp-OutputArea-output dt,
    .jp-OutputArea-output dd {
    display: block;
    }

    .jp-OutputArea-output dl {
    width: 100%;
    overflow: hidden;
    padding: 0;
    margin: 0;
    }

    .jp-OutputArea-output dt {
    font-weight: bold;
    float: left;
    width: 20%;
    padding: 0;
    margin: 0;
    }

    .jp-OutputArea-output dd {
    float: left;
    width: 80%;
    padding: 0;
    margin: 0;
    }

    .jp-TrimmedOutputs pre {
    background: var(--jp-layout-color3);
    font-size: calc(var(--jp-code-font-size) * 1.4);
    text-align: center;
    text-transform: uppercase;
    }

    /* Hide the gutter in case of
    *  - nested output areas (e.g. in the case of output widgets)
    *  - mirrored output areas
    */
    .jp-OutputArea .jp-OutputArea .jp-OutputArea-prompt {
    display: none;
    }

    /* Hide empty lines in the output area, for instance due to cleared widgets */
    .jp-OutputArea-prompt:empty {
    padding: 0;
    border: 0;
    }

    /*-----------------------------------------------------------------------------
    | executeResult is added to any Output-result for the display of the object
    | returned by a cell
    |----------------------------------------------------------------------------*/

    .jp-OutputArea-output.jp-OutputArea-executeResult {
    margin-left: 0;
    width: 100%;
    }

    /* Text output with the Out[] prompt needs a top padding to match the
    * alignment of the Out[] prompt itself.
    */
    .jp-OutputArea-executeResult .jp-RenderedText.jp-OutputArea-output {
    padding-top: var(--jp-code-padding);
    border-top: var(--jp-border-width) solid transparent;
    }

    /*-----------------------------------------------------------------------------
    | The Stdin output
    |----------------------------------------------------------------------------*/

    .jp-Stdin-prompt {
    color: var(--jp-content-font-color0);
    padding-right: var(--jp-code-padding);
    vertical-align: baseline;
    flex: 0 0 auto;
    }

    .jp-Stdin-input {
    font-family: var(--jp-code-font-family);
    font-size: inherit;
    color: inherit;
    background-color: inherit;
    width: 42%;
    min-width: 200px;

    /* make sure input baseline aligns with prompt */
    vertical-align: baseline;

    /* padding + margin = 0.5em between prompt and cursor */
    padding: 0 0.25em;
    margin: 0 0.25em;
    flex: 0 0 70%;
    }

    .jp-Stdin-input::placeholder {
    opacity: 0;
    }

    .jp-Stdin-input:focus {
    box-shadow: none;
    }

    .jp-Stdin-input:focus::placeholder {
    opacity: 1;
    }

    /*-----------------------------------------------------------------------------
    | Output Area View
    |----------------------------------------------------------------------------*/

    .jp-LinkedOutputView .jp-OutputArea {
    height: 100%;
    display: block;
    }

    .jp-LinkedOutputView .jp-OutputArea-output:only-child {
    height: 100%;
    }

    /*-----------------------------------------------------------------------------
    | Printing
    |----------------------------------------------------------------------------*/

    @media print {
    .jp-OutputArea-child {
        break-inside: avoid-page;
    }
    }

    /*-----------------------------------------------------------------------------
    | Mobile
    |----------------------------------------------------------------------------*/
    @media only screen and (max-width: 760px) {
    .jp-OutputPrompt {
        display: table-row;
        text-align: left;
    }

    .jp-OutputArea-child .jp-OutputArea-output {
        display: table-row;
        margin-left: var(--jp-notebook-padding);
    }
    }

    /* Trimmed outputs warning */
    .jp-TrimmedOutputs > a {
    margin: 10px;
    text-decoration: none;
    cursor: pointer;
    }

    .jp-TrimmedOutputs > a:hover {
    text-decoration: none;
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    /*-----------------------------------------------------------------------------
    | Table of Contents
    |----------------------------------------------------------------------------*/

    :root {
    --jp-private-toc-active-width: 4px;
    }

    .jp-TableOfContents {
    display: flex;
    flex-direction: column;
    background: var(--jp-layout-color1);
    color: var(--jp-ui-font-color1);
    font-size: var(--jp-ui-font-size1);
    height: 100%;
    }

    .jp-TableOfContents-placeholder {
    text-align: center;
    }

    .jp-TableOfContents-placeholderContent {
    color: var(--jp-content-font-color2);
    padding: 8px;
    }

    .jp-TableOfContents-placeholderContent > h3 {
    margin-bottom: var(--jp-content-heading-margin-bottom);
    }

    .jp-TableOfContents .jp-SidePanel-content {
    overflow-y: auto;
    }

    .jp-TableOfContents-tree {
    margin: 4px;
    }

    .jp-TableOfContents ol {
    list-style-type: none;
    }

    /* stylelint-disable-next-line selector-max-type */
    .jp-TableOfContents li > ol {
    /* Align left border with triangle icon center */
    padding-left: 11px;
    }

    .jp-TableOfContents-content {
    /* left margin for the active heading indicator */
    margin: 0 0 0 var(--jp-private-toc-active-width);
    padding: 0;
    background-color: var(--jp-layout-color1);
    }

    .jp-tocItem {
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    }

    .jp-tocItem-heading {
    display: flex;
    cursor: pointer;
    }

    .jp-tocItem-heading:hover {
    background-color: var(--jp-layout-color2);
    }

    .jp-tocItem-content {
    display: block;
    padding: 4px 0;
    white-space: nowrap;
    text-overflow: ellipsis;
    overflow-x: hidden;
    }

    .jp-tocItem-collapser {
    height: 20px;
    margin: 2px 2px 0;
    padding: 0;
    background: none;
    border: none;
    cursor: pointer;
    }

    .jp-tocItem-collapser:hover {
    background-color: var(--jp-layout-color3);
    }

    /* Active heading indicator */

    .jp-tocItem-heading::before {
    content: ' ';
    background: transparent;
    width: var(--jp-private-toc-active-width);
    height: 24px;
    position: absolute;
    left: 0;
    border-radius: var(--jp-border-radius);
    }

    .jp-tocItem-heading.jp-tocItem-active::before {
    background-color: var(--jp-brand-color1);
    }

    .jp-tocItem-heading:hover.jp-tocItem-active::before {
    background: var(--jp-brand-color0);
    opacity: 1;
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    .jp-Collapser {
    flex: 0 0 var(--jp-cell-collapser-width);
    padding: 0;
    margin: 0;
    border: none;
    outline: none;
    background: transparent;
    border-radius: var(--jp-border-radius);
    opacity: 1;
    }

    .jp-Collapser-child {
    display: block;
    width: 100%;
    box-sizing: border-box;

    /* height: 100% doesn't work because the height of its parent is computed from content */
    position: absolute;
    top: 0;
    bottom: 0;
    }

    /*-----------------------------------------------------------------------------
    | Printing
    |----------------------------------------------------------------------------*/

    /*
    Hiding collapsers in print mode.

    Note: input and output wrappers have "display: block" propery in print mode.
    */

    @media print {
    .jp-Collapser {
        display: none;
    }
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    /*-----------------------------------------------------------------------------
    | Header/Footer
    |----------------------------------------------------------------------------*/

    /* Hidden by zero height by default */
    .jp-CellHeader,
    .jp-CellFooter {
    height: 0;
    width: 100%;
    padding: 0;
    margin: 0;
    border: none;
    outline: none;
    background: transparent;
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    /*-----------------------------------------------------------------------------
    | Input
    |----------------------------------------------------------------------------*/

    /* All input areas */
    .jp-InputArea {
    display: table;
    table-layout: fixed;
    width: 100%;
    overflow: hidden;
    }

    .jp-InputArea-editor {
    display: table-cell;
    overflow: hidden;
    vertical-align: top;

    /* This is the non-active, default styling */
    border: var(--jp-border-width) solid var(--jp-cell-editor-border-color);
    border-radius: 0;
    background: var(--jp-cell-editor-background);
    }

    .jp-InputPrompt {
    display: table-cell;
    vertical-align: top;
    width: var(--jp-cell-prompt-width);
    color: var(--jp-cell-inprompt-font-color);
    font-family: var(--jp-cell-prompt-font-family);
    padding: var(--jp-code-padding);
    letter-spacing: var(--jp-cell-prompt-letter-spacing);
    opacity: var(--jp-cell-prompt-opacity);
    line-height: var(--jp-code-line-height);
    font-size: var(--jp-code-font-size);
    border: var(--jp-border-width) solid transparent;

    /* Right align prompt text, don't wrap to handle large prompt numbers */
    text-align: right;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;

    /* Disable text selection */
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    }

    /*-----------------------------------------------------------------------------
    | Mobile
    |----------------------------------------------------------------------------*/
    @media only screen and (max-width: 760px) {
    .jp-InputArea-editor {
        display: table-row;
        margin-left: var(--jp-notebook-padding);
    }

    .jp-InputPrompt {
        display: table-row;
        text-align: left;
    }
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    /*-----------------------------------------------------------------------------
    | Placeholder
    |----------------------------------------------------------------------------*/

    .jp-Placeholder {
    display: table;
    table-layout: fixed;
    width: 100%;
    }

    .jp-Placeholder-prompt {
    display: table-cell;
    box-sizing: border-box;
    }

    .jp-Placeholder-content {
    display: table-cell;
    padding: 4px 6px;
    border: 1px solid transparent;
    border-radius: 0;
    background: none;
    box-sizing: border-box;
    cursor: pointer;
    }

    .jp-Placeholder-contentContainer {
    display: flex;
    }

    .jp-Placeholder-content:hover,
    .jp-InputPlaceholder > .jp-Placeholder-content:hover {
    border-color: var(--jp-layout-color3);
    }

    .jp-Placeholder-content .jp-MoreHorizIcon {
    width: 32px;
    height: 16px;
    border: 1px solid transparent;
    border-radius: var(--jp-border-radius);
    }

    .jp-Placeholder-content .jp-MoreHorizIcon:hover {
    border: 1px solid var(--jp-border-color1);
    box-shadow: 0 0 2px 0 rgba(0, 0, 0, 0.25);
    background-color: var(--jp-layout-color0);
    }

    .jp-PlaceholderText {
    white-space: nowrap;
    overflow-x: hidden;
    color: var(--jp-inverse-layout-color3);
    font-family: var(--jp-code-font-family);
    }

    .jp-InputPlaceholder > .jp-Placeholder-content {
    border-color: var(--jp-cell-editor-border-color);
    background: var(--jp-cell-editor-background);
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    /*-----------------------------------------------------------------------------
    | Private CSS variables
    |----------------------------------------------------------------------------*/

    :root {
    --jp-private-cell-scrolling-output-offset: 5px;
    }

    /*-----------------------------------------------------------------------------
    | Cell
    |----------------------------------------------------------------------------*/

    .jp-Cell {
    padding: var(--jp-cell-padding);
    margin: 0;
    border: none;
    outline: none;
    background: transparent;
    }

    /*-----------------------------------------------------------------------------
    | Common input/output
    |----------------------------------------------------------------------------*/

    .jp-Cell-inputWrapper,
    .jp-Cell-outputWrapper {
    display: flex;
    flex-direction: row;
    padding: 0;
    margin: 0;

    /* Added to reveal the box-shadow on the input and output collapsers. */
    overflow: visible;
    }

    /* Only input/output areas inside cells */
    .jp-Cell-inputArea,
    .jp-Cell-outputArea {
    flex: 1 1 auto;
    }

    /*-----------------------------------------------------------------------------
    | Collapser
    |----------------------------------------------------------------------------*/

    /* Make the output collapser disappear when there is not output, but do so
    * in a manner that leaves it in the layout and preserves its width.
    */
    .jp-Cell.jp-mod-noOutputs .jp-Cell-outputCollapser {
    border: none !important;
    background: transparent !important;
    }

    .jp-Cell:not(.jp-mod-noOutputs) .jp-Cell-outputCollapser {
    min-height: var(--jp-cell-collapser-min-height);
    }

    /*-----------------------------------------------------------------------------
    | Output
    |----------------------------------------------------------------------------*/

    /* Put a space between input and output when there IS output */
    .jp-Cell:not(.jp-mod-noOutputs) .jp-Cell-outputWrapper {
    margin-top: 5px;
    }

    .jp-CodeCell.jp-mod-outputsScrolled .jp-Cell-outputArea {
    overflow-y: auto;
    max-height: 24em;
    margin-left: var(--jp-private-cell-scrolling-output-offset);
    resize: vertical;
    }

    .jp-CodeCell.jp-mod-outputsScrolled .jp-Cell-outputArea[style*='height'] {
    max-height: unset;
    }

    .jp-CodeCell.jp-mod-outputsScrolled .jp-Cell-outputArea::after {
    content: ' ';
    box-shadow: inset 0 0 6px 2px rgb(0 0 0 / 30%);
    width: 100%;
    height: 100%;
    position: sticky;
    bottom: 0;
    top: 0;
    margin-top: -50%;
    float: left;
    display: block;
    pointer-events: none;
    }

    .jp-CodeCell.jp-mod-outputsScrolled .jp-OutputArea-child {
    padding-top: 6px;
    }

    .jp-CodeCell.jp-mod-outputsScrolled .jp-OutputArea-prompt {
    width: calc(
        var(--jp-cell-prompt-width) - var(--jp-private-cell-scrolling-output-offset)
    );
    }

    .jp-CodeCell.jp-mod-outputsScrolled .jp-OutputArea-promptOverlay {
    left: calc(-1 * var(--jp-private-cell-scrolling-output-offset));
    }

    /*-----------------------------------------------------------------------------
    | CodeCell
    |----------------------------------------------------------------------------*/

    /*-----------------------------------------------------------------------------
    | MarkdownCell
    |----------------------------------------------------------------------------*/

    .jp-MarkdownOutput {
    display: table-cell;
    width: 100%;
    margin-top: 0;
    margin-bottom: 0;
    padding-left: var(--jp-code-padding);
    }

    .jp-MarkdownOutput.jp-RenderedHTMLCommon {
    overflow: auto;
    }

    /* collapseHeadingButton (show always if hiddenCellsButton is _not_ shown) */
    .jp-collapseHeadingButton {
    display: flex;
    min-height: var(--jp-cell-collapser-min-height);
    font-size: var(--jp-code-font-size);
    position: absolute;
    background-color: transparent;
    background-size: 25px;
    background-repeat: no-repeat;
    background-position-x: center;
    background-position-y: top;
    background-image: var(--jp-icon-caret-down);
    right: 0;
    top: 0;
    bottom: 0;
    }

    .jp-collapseHeadingButton.jp-mod-collapsed {
    background-image: var(--jp-icon-caret-right);
    }

    /*
    set the container font size to match that of content
    so that the nested collapse buttons have the right size
    */
    .jp-MarkdownCell .jp-InputPrompt {
    font-size: var(--jp-content-font-size1);
    }

    /*
    Align collapseHeadingButton with cell top header
    The font sizes are identical to the ones in packages/rendermime/style/base.css
    */
    .jp-mod-rendered .jp-collapseHeadingButton[data-heading-level='1'] {
    font-size: var(--jp-content-font-size5);
    background-position-y: calc(0.3 * var(--jp-content-font-size5));
    }

    .jp-mod-rendered .jp-collapseHeadingButton[data-heading-level='2'] {
    font-size: var(--jp-content-font-size4);
    background-position-y: calc(0.3 * var(--jp-content-font-size4));
    }

    .jp-mod-rendered .jp-collapseHeadingButton[data-heading-level='3'] {
    font-size: var(--jp-content-font-size3);
    background-position-y: calc(0.3 * var(--jp-content-font-size3));
    }

    .jp-mod-rendered .jp-collapseHeadingButton[data-heading-level='4'] {
    font-size: var(--jp-content-font-size2);
    background-position-y: calc(0.3 * var(--jp-content-font-size2));
    }

    .jp-mod-rendered .jp-collapseHeadingButton[data-heading-level='5'] {
    font-size: var(--jp-content-font-size1);
    background-position-y: top;
    }

    .jp-mod-rendered .jp-collapseHeadingButton[data-heading-level='6'] {
    font-size: var(--jp-content-font-size0);
    background-position-y: top;
    }

    /* collapseHeadingButton (show only on (hover,active) if hiddenCellsButton is shown) */
    .jp-Notebook.jp-mod-showHiddenCellsButton .jp-collapseHeadingButton {
    display: none;
    }

    .jp-Notebook.jp-mod-showHiddenCellsButton
    :is(.jp-MarkdownCell:hover, .jp-mod-active)
    .jp-collapseHeadingButton {
    display: flex;
    }

    /* showHiddenCellsButton (only show if jp-mod-showHiddenCellsButton is set, which
    is a consequence of the showHiddenCellsButton option in Notebook Settings)*/
    .jp-Notebook.jp-mod-showHiddenCellsButton .jp-showHiddenCellsButton {
    margin-left: calc(var(--jp-cell-prompt-width) + 2 * var(--jp-code-padding));
    margin-top: var(--jp-code-padding);
    border: 1px solid var(--jp-border-color2);
    background-color: var(--jp-border-color3) !important;
    color: var(--jp-content-font-color0) !important;
    display: flex;
    }

    .jp-Notebook.jp-mod-showHiddenCellsButton .jp-showHiddenCellsButton:hover {
    background-color: var(--jp-border-color2) !important;
    }

    .jp-showHiddenCellsButton {
    display: none;
    }

    /*-----------------------------------------------------------------------------
    | Printing
    |----------------------------------------------------------------------------*/

    /*
    Using block instead of flex to allow the use of the break-inside CSS property for
    cell outputs.
    */

    @media print {
    .jp-Cell-inputWrapper,
    .jp-Cell-outputWrapper {
        display: block;
    }
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    /*-----------------------------------------------------------------------------
    | Variables
    |----------------------------------------------------------------------------*/

    :root {
    --jp-notebook-toolbar-padding: 2px 5px 2px 2px;
    }

    /*-----------------------------------------------------------------------------

    /*-----------------------------------------------------------------------------
    | Styles
    |----------------------------------------------------------------------------*/

    .jp-NotebookPanel-toolbar {
    padding: var(--jp-notebook-toolbar-padding);

    /* disable paint containment from lumino 2.0 default strict CSS containment */
    contain: style size !important;
    }

    .jp-Toolbar-item.jp-Notebook-toolbarCellType .jp-select-wrapper.jp-mod-focused {
    border: none;
    box-shadow: none;
    }

    .jp-Notebook-toolbarCellTypeDropdown select {
    height: 24px;
    font-size: var(--jp-ui-font-size1);
    line-height: 14px;
    border-radius: 0;
    display: block;
    }

    .jp-Notebook-toolbarCellTypeDropdown span {
    top: 5px !important;
    }

    .jp-Toolbar-responsive-popup {
    position: absolute;
    height: fit-content;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: flex-end;
    border-bottom: var(--jp-border-width) solid var(--jp-toolbar-border-color);
    box-shadow: var(--jp-toolbar-box-shadow);
    background: var(--jp-toolbar-background);
    min-height: var(--jp-toolbar-micro-height);
    padding: var(--jp-notebook-toolbar-padding);
    z-index: 1;
    right: 0;
    top: 0;
    }

    .jp-Toolbar > .jp-Toolbar-responsive-opener {
    margin-left: auto;
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    /*-----------------------------------------------------------------------------
    | Variables
    |----------------------------------------------------------------------------*/

    /*-----------------------------------------------------------------------------

    /*-----------------------------------------------------------------------------
    | Styles
    |----------------------------------------------------------------------------*/

    .jp-Notebook-ExecutionIndicator {
    position: relative;
    display: inline-block;
    height: 100%;
    z-index: 9997;
    }

    .jp-Notebook-ExecutionIndicator-tooltip {
    visibility: hidden;
    height: auto;
    width: max-content;
    width: -moz-max-content;
    background-color: var(--jp-layout-color2);
    color: var(--jp-ui-font-color1);
    text-align: justify;
    border-radius: 6px;
    padding: 0 5px;
    position: fixed;
    display: table;
    }

    .jp-Notebook-ExecutionIndicator-tooltip.up {
    transform: translateX(-50%) translateY(-100%) translateY(-32px);
    }

    .jp-Notebook-ExecutionIndicator-tooltip.down {
    transform: translateX(calc(-100% + 16px)) translateY(5px);
    }

    .jp-Notebook-ExecutionIndicator-tooltip.hidden {
    display: none;
    }

    .jp-Notebook-ExecutionIndicator:hover .jp-Notebook-ExecutionIndicator-tooltip {
    visibility: visible;
    }

    .jp-Notebook-ExecutionIndicator span {
    font-size: var(--jp-ui-font-size1);
    font-family: var(--jp-ui-font-family);
    color: var(--jp-ui-font-color1);
    line-height: 24px;
    display: block;
    }

    .jp-Notebook-ExecutionIndicator-progress-bar {
    display: flex;
    justify-content: center;
    height: 100%;
    }

    /*
    * Copyright (c) Jupyter Development Team.
    * Distributed under the terms of the Modified BSD License.
    */

    /*
    * Execution indicator
    */
    .jp-tocItem-content::after {
    content: '';

    /* Must be identical to form a circle */
    width: 12px;
    height: 12px;
    background: none;
    border: none;
    position: absolute;
    right: 0;
    }

    .jp-tocItem-content[data-running='0']::after {
    border-radius: 50%;
    border: var(--jp-border-width) solid var(--jp-inverse-layout-color3);
    background: none;
    }

    .jp-tocItem-content[data-running='1']::after {
    border-radius: 50%;
    border: var(--jp-border-width) solid var(--jp-inverse-layout-color3);
    background-color: var(--jp-inverse-layout-color3);
    }

    .jp-tocItem-content[data-running='0'],
    .jp-tocItem-content[data-running='1'] {
    margin-right: 12px;
    }

    /*
    * Copyright (c) Jupyter Development Team.
    * Distributed under the terms of the Modified BSD License.
    */

    .jp-Notebook-footer {
    height: 27px;
    margin-left: calc(
        var(--jp-cell-prompt-width) + var(--jp-cell-collapser-width) +
        var(--jp-cell-padding)
    );
    width: calc(
        100% -
        (
            var(--jp-cell-prompt-width) + var(--jp-cell-collapser-width) +
            var(--jp-cell-padding) + var(--jp-cell-padding)
        )
    );
    border: var(--jp-border-width) solid var(--jp-cell-editor-border-color);
    color: var(--jp-ui-font-color3);
    margin-top: 6px;
    background: none;
    cursor: pointer;
    }

    .jp-Notebook-footer:focus {
    border-color: var(--jp-cell-editor-active-border-color);
    }

    /* For devices that support hovering, hide footer until hover */
    @media (hover: hover) {
    .jp-Notebook-footer {
        opacity: 0;
    }

    .jp-Notebook-footer:focus,
    .jp-Notebook-footer:hover {
        opacity: 1;
    }
    }

    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    /*-----------------------------------------------------------------------------
    | Imports
    |----------------------------------------------------------------------------*/

    /*-----------------------------------------------------------------------------
    | CSS variables
    |----------------------------------------------------------------------------*/

    :root {
    --jp-side-by-side-output-size: 1fr;
    --jp-side-by-side-resized-cell: var(--jp-side-by-side-output-size);
    --jp-private-notebook-dragImage-width: 304px;
    --jp-private-notebook-dragImage-height: 36px;
    --jp-private-notebook-selected-color: var(--md-blue-400);
    --jp-private-notebook-active-color: var(--md-green-400);
    }

    /*-----------------------------------------------------------------------------
    | Notebook
    |----------------------------------------------------------------------------*/

    /* stylelint-disable selector-max-class */

    .jp-NotebookPanel {
    display: block;
    height: 100%;
    }

    .jp-NotebookPanel.jp-Document {
    min-width: 240px;
    min-height: 120px;
    }

    .jp-Notebook {
    padding: var(--jp-notebook-padding);
    outline: none;
    overflow: auto;
    background: var(--jp-layout-color0);
    }

    .jp-Notebook.jp-mod-scrollPastEnd::after {
    display: block;
    content: '';
    min-height: var(--jp-notebook-scroll-padding);
    }

    .jp-MainAreaWidget-ContainStrict .jp-Notebook * {
    contain: strict;
    }

    .jp-Notebook .jp-Cell {
    overflow: visible;
    }

    .jp-Notebook .jp-Cell .jp-InputPrompt {
    cursor: move;
    }

    /*-----------------------------------------------------------------------------
    | Notebook state related styling
    |
    | The notebook and cells each have states, here are the possibilities:
    |
    | - Notebook
    |   - Command
    |   - Edit
    | - Cell
    |   - None
    |   - Active (only one can be active)
    |   - Selected (the cells actions are applied to)
    |   - Multiselected (when multiple selected, the cursor)
    |   - No outputs
    |----------------------------------------------------------------------------*/

    /* Command or edit modes */

    .jp-Notebook .jp-Cell:not(.jp-mod-active) .jp-InputPrompt {
    opacity: var(--jp-cell-prompt-not-active-opacity);
    color: var(--jp-cell-prompt-not-active-font-color);
    }

    .jp-Notebook .jp-Cell:not(.jp-mod-active) .jp-OutputPrompt {
    opacity: var(--jp-cell-prompt-not-active-opacity);
    color: var(--jp-cell-prompt-not-active-font-color);
    }

    /* cell is active */
    .jp-Notebook .jp-Cell.jp-mod-active .jp-Collapser {
    background: var(--jp-brand-color1);
    }

    /* cell is dirty */
    .jp-Notebook .jp-Cell.jp-mod-dirty .jp-InputPrompt {
    color: var(--jp-warn-color1);
    }

    .jp-Notebook .jp-Cell.jp-mod-dirty .jp-InputPrompt::before {
    color: var(--jp-warn-color1);
    content: '•';
    }

    .jp-Notebook .jp-Cell.jp-mod-active.jp-mod-dirty .jp-Collapser {
    background: var(--jp-warn-color1);
    }

    /* collapser is hovered */
    .jp-Notebook .jp-Cell .jp-Collapser:hover {
    box-shadow: var(--jp-elevation-z2);
    background: var(--jp-brand-color1);
    opacity: var(--jp-cell-collapser-not-active-hover-opacity);
    }

    /* cell is active and collapser is hovered */
    .jp-Notebook .jp-Cell.jp-mod-active .jp-Collapser:hover {
    background: var(--jp-brand-color0);
    opacity: 1;
    }

    /* Command mode */

    .jp-Notebook.jp-mod-commandMode .jp-Cell.jp-mod-selected {
    background: var(--jp-notebook-multiselected-color);
    }

    .jp-Notebook.jp-mod-commandMode
    .jp-Cell.jp-mod-active.jp-mod-selected:not(.jp-mod-multiSelected) {
    background: transparent;
    }

    /* Edit mode */

    .jp-Notebook.jp-mod-editMode .jp-Cell.jp-mod-active .jp-InputArea-editor {
    border: var(--jp-border-width) solid var(--jp-cell-editor-active-border-color);
    box-shadow: var(--jp-input-box-shadow);
    background-color: var(--jp-cell-editor-active-background);
    }

    /*-----------------------------------------------------------------------------
    | Notebook drag and drop
    |----------------------------------------------------------------------------*/

    .jp-Notebook-cell.jp-mod-dropSource {
    opacity: 0.5;
    }

    .jp-Notebook-cell.jp-mod-dropTarget,
    .jp-Notebook.jp-mod-commandMode
    .jp-Notebook-cell.jp-mod-active.jp-mod-selected.jp-mod-dropTarget {
    border-top-color: var(--jp-private-notebook-selected-color);
    border-top-style: solid;
    border-top-width: 2px;
    }

    .jp-dragImage {
    display: block;
    flex-direction: row;
    width: var(--jp-private-notebook-dragImage-width);
    height: var(--jp-private-notebook-dragImage-height);
    border: var(--jp-border-width) solid var(--jp-cell-editor-border-color);
    background: var(--jp-cell-editor-background);
    overflow: visible;
    }

    .jp-dragImage-singlePrompt {
    box-shadow: 2px 2px 4px 0 rgba(0, 0, 0, 0.12);
    }

    .jp-dragImage .jp-dragImage-content {
    flex: 1 1 auto;
    z-index: 2;
    font-size: var(--jp-code-font-size);
    font-family: var(--jp-code-font-family);
    line-height: var(--jp-code-line-height);
    padding: var(--jp-code-padding);
    border: var(--jp-border-width) solid var(--jp-cell-editor-border-color);
    background: var(--jp-cell-editor-background-color);
    color: var(--jp-content-font-color3);
    text-align: left;
    margin: 4px 4px 4px 0;
    }

    .jp-dragImage .jp-dragImage-prompt {
    flex: 0 0 auto;
    min-width: 36px;
    color: var(--jp-cell-inprompt-font-color);
    padding: var(--jp-code-padding);
    padding-left: 12px;
    font-family: var(--jp-cell-prompt-font-family);
    letter-spacing: var(--jp-cell-prompt-letter-spacing);
    line-height: 1.9;
    font-size: var(--jp-code-font-size);
    border: var(--jp-border-width) solid transparent;
    }

    .jp-dragImage-multipleBack {
    z-index: -1;
    position: absolute;
    height: 32px;
    width: 300px;
    top: 8px;
    left: 8px;
    background: var(--jp-layout-color2);
    border: var(--jp-border-width) solid var(--jp-input-border-color);
    box-shadow: 2px 2px 4px 0 rgba(0, 0, 0, 0.12);
    }

    /*-----------------------------------------------------------------------------
    | Cell toolbar
    |----------------------------------------------------------------------------*/

    .jp-NotebookTools {
    display: block;
    min-width: var(--jp-sidebar-min-width);
    color: var(--jp-ui-font-color1);
    background: var(--jp-layout-color1);

    /* This is needed so that all font sizing of children done in ems is
        * relative to this base size */
    font-size: var(--jp-ui-font-size1);
    overflow: auto;
    }

    .jp-ActiveCellTool {
    padding: 12px 0;
    display: flex;
    }

    .jp-ActiveCellTool-Content {
    flex: 1 1 auto;
    }

    .jp-ActiveCellTool .jp-ActiveCellTool-CellContent {
    background: var(--jp-cell-editor-background);
    border: var(--jp-border-width) solid var(--jp-cell-editor-border-color);
    border-radius: 0;
    min-height: 29px;
    }

    .jp-ActiveCellTool .jp-InputPrompt {
    min-width: calc(var(--jp-cell-prompt-width) * 0.75);
    }

    .jp-ActiveCellTool-CellContent > pre {
    padding: 5px 4px;
    margin: 0;
    white-space: normal;
    }

    .jp-MetadataEditorTool {
    flex-direction: column;
    padding: 12px 0;
    }

    .jp-RankedPanel > :not(:first-child) {
    margin-top: 12px;
    }

    .jp-KeySelector select.jp-mod-styled {
    font-size: var(--jp-ui-font-size1);
    color: var(--jp-ui-font-color0);
    border: var(--jp-border-width) solid var(--jp-border-color1);
    }

    .jp-KeySelector label,
    .jp-MetadataEditorTool label,
    .jp-NumberSetter label {
    line-height: 1.4;
    }

    .jp-NotebookTools .jp-select-wrapper {
    margin-top: 4px;
    margin-bottom: 0;
    }

    .jp-NumberSetter input {
    width: 100%;
    margin-top: 4px;
    }

    .jp-NotebookTools .jp-Collapse {
    margin-top: 16px;
    }

    /*-----------------------------------------------------------------------------
    | Presentation Mode (.jp-mod-presentationMode)
    |----------------------------------------------------------------------------*/

    .jp-mod-presentationMode .jp-Notebook {
    --jp-content-font-size1: var(--jp-content-presentation-font-size1);
    --jp-code-font-size: var(--jp-code-presentation-font-size);
    }

    .jp-mod-presentationMode .jp-Notebook .jp-Cell .jp-InputPrompt,
    .jp-mod-presentationMode .jp-Notebook .jp-Cell .jp-OutputPrompt {
    flex: 0 0 110px;
    }

    /*-----------------------------------------------------------------------------
    | Side-by-side Mode (.jp-mod-sideBySide)
    |----------------------------------------------------------------------------*/
    .jp-mod-sideBySide.jp-Notebook .jp-Notebook-cell {
    margin-top: 3em;
    margin-bottom: 3em;
    margin-left: 5%;
    margin-right: 5%;
    }

    .jp-mod-sideBySide.jp-Notebook .jp-CodeCell {
    display: grid;
    grid-template-columns: minmax(0, 1fr) min-content minmax(
        0,
        var(--jp-side-by-side-output-size)
        );
    grid-template-rows: auto minmax(0, 1fr) auto;
    grid-template-areas:
        'header header header'
        'input handle output'
        'footer footer footer';
    }

    .jp-mod-sideBySide.jp-Notebook .jp-CodeCell.jp-mod-resizedCell {
    grid-template-columns: minmax(0, 1fr) min-content minmax(
        0,
        var(--jp-side-by-side-resized-cell)
        );
    }

    .jp-mod-sideBySide.jp-Notebook .jp-CodeCell .jp-CellHeader {
    grid-area: header;
    }

    .jp-mod-sideBySide.jp-Notebook .jp-CodeCell .jp-Cell-inputWrapper {
    grid-area: input;
    }

    .jp-mod-sideBySide.jp-Notebook .jp-CodeCell .jp-Cell-outputWrapper {
    /* overwrite the default margin (no vertical separation needed in side by side move */
    margin-top: 0;
    grid-area: output;
    }

    .jp-mod-sideBySide.jp-Notebook .jp-CodeCell .jp-CellFooter {
    grid-area: footer;
    }

    .jp-mod-sideBySide.jp-Notebook .jp-CodeCell .jp-CellResizeHandle {
    grid-area: handle;
    user-select: none;
    display: block;
    height: 100%;
    cursor: ew-resize;
    padding: 0 var(--jp-cell-padding);
    }

    .jp-mod-sideBySide.jp-Notebook .jp-CodeCell .jp-CellResizeHandle::after {
    content: '';
    display: block;
    background: var(--jp-border-color2);
    height: 100%;
    width: 5px;
    }

    .jp-mod-sideBySide.jp-Notebook
    .jp-CodeCell.jp-mod-resizedCell
    .jp-CellResizeHandle::after {
    background: var(--jp-border-color0);
    }

    .jp-CellResizeHandle {
    display: none;
    }

    /*-----------------------------------------------------------------------------
    | Placeholder
    |----------------------------------------------------------------------------*/

    .jp-Cell-Placeholder {
    padding-left: 55px;
    }

    .jp-Cell-Placeholder-wrapper {
    background: #fff;
    border: 1px solid;
    border-color: #e5e6e9 #dfe0e4 #d0d1d5;
    border-radius: 4px;
    -webkit-border-radius: 4px;
    margin: 10px 15px;
    }

    .jp-Cell-Placeholder-wrapper-inner {
    padding: 15px;
    position: relative;
    }

    .jp-Cell-Placeholder-wrapper-body {
    background-repeat: repeat;
    background-size: 50% auto;
    }

    .jp-Cell-Placeholder-wrapper-body div {
    background: #f6f7f8;
    background-image: -webkit-linear-gradient(
        left,
        #f6f7f8 0%,
        #edeef1 20%,
        #f6f7f8 40%,
        #f6f7f8 100%
    );
    background-repeat: no-repeat;
    background-size: 800px 104px;
    height: 104px;
    position: absolute;
    right: 15px;
    left: 15px;
    top: 15px;
    }

    div.jp-Cell-Placeholder-h1 {
    top: 20px;
    height: 20px;
    left: 15px;
    width: 150px;
    }

    div.jp-Cell-Placeholder-h2 {
    left: 15px;
    top: 50px;
    height: 10px;
    width: 100px;
    }

    div.jp-Cell-Placeholder-content-1,
    div.jp-Cell-Placeholder-content-2,
    div.jp-Cell-Placeholder-content-3 {
    left: 15px;
    right: 15px;
    height: 10px;
    }

    div.jp-Cell-Placeholder-content-1 {
    top: 100px;
    }

    div.jp-Cell-Placeholder-content-2 {
    top: 120px;
    }

    div.jp-Cell-Placeholder-content-3 {
    top: 140px;
    }

    </style>
    <style type="text/css">
    /*-----------------------------------------------------------------------------
    | Copyright (c) Jupyter Development Team.
    | Distributed under the terms of the Modified BSD License.
    |----------------------------------------------------------------------------*/

    /*
    The following CSS variables define the main, public API for styling JupyterLab.
    These variables should be used by all plugins wherever possible. In other
    words, plugins should not define custom colors, sizes, etc unless absolutely
    necessary. This enables users to change the visual theme of JupyterLab
    by changing these variables.

    Many variables appear in an ordered sequence (0,1,2,3). These sequences
    are designed to work well together, so for example, `--jp-border-color1` should
    be used with `--jp-layout-color1`. The numbers have the following meanings:

    * 0: super-primary, reserved for special emphasis
    * 1: primary, most important under normal situations
    * 2: secondary, next most important under normal situations
    * 3: tertiary, next most important under normal situations

    Throughout JupyterLab, we are mostly following principles from Google's
    Material Design when selecting colors. We are not, however, following
    all of MD as it is not optimized for dense, information rich UIs.
    */

    :root {
    /* Elevation
    *
    * We style box-shadows using Material Design's idea of elevation. These particular numbers are taken from here:
    *
    * https://github.com/material-components/material-components-web
    * https://material-components-web.appspot.com/elevation.html
    */

    --jp-shadow-base-lightness: 0;
    --jp-shadow-umbra-color: rgba(
        var(--jp-shadow-base-lightness),
        var(--jp-shadow-base-lightness),
        var(--jp-shadow-base-lightness),
        0.2
    );
    --jp-shadow-penumbra-color: rgba(
        var(--jp-shadow-base-lightness),
        var(--jp-shadow-base-lightness),
        var(--jp-shadow-base-lightness),
        0.14
    );
    --jp-shadow-ambient-color: rgba(
        var(--jp-shadow-base-lightness),
        var(--jp-shadow-base-lightness),
        var(--jp-shadow-base-lightness),
        0.12
    );
    --jp-elevation-z0: none;
    --jp-elevation-z1: 0 2px 1px -1px var(--jp-shadow-umbra-color),
        0 1px 1px 0 var(--jp-shadow-penumbra-color),
        0 1px 3px 0 var(--jp-shadow-ambient-color);
    --jp-elevation-z2: 0 3px 1px -2px var(--jp-shadow-umbra-color),
        0 2px 2px 0 var(--jp-shadow-penumbra-color),
        0 1px 5px 0 var(--jp-shadow-ambient-color);
    --jp-elevation-z4: 0 2px 4px -1px var(--jp-shadow-umbra-color),
        0 4px 5px 0 var(--jp-shadow-penumbra-color),
        0 1px 10px 0 var(--jp-shadow-ambient-color);
    --jp-elevation-z6: 0 3px 5px -1px var(--jp-shadow-umbra-color),
        0 6px 10px 0 var(--jp-shadow-penumbra-color),
        0 1px 18px 0 var(--jp-shadow-ambient-color);
    --jp-elevation-z8: 0 5px 5px -3px var(--jp-shadow-umbra-color),
        0 8px 10px 1px var(--jp-shadow-penumbra-color),
        0 3px 14px 2px var(--jp-shadow-ambient-color);
    --jp-elevation-z12: 0 7px 8px -4px var(--jp-shadow-umbra-color),
        0 12px 17px 2px var(--jp-shadow-penumbra-color),
        0 5px 22px 4px var(--jp-shadow-ambient-color);
    --jp-elevation-z16: 0 8px 10px -5px var(--jp-shadow-umbra-color),
        0 16px 24px 2px var(--jp-shadow-penumbra-color),
        0 6px 30px 5px var(--jp-shadow-ambient-color);
    --jp-elevation-z20: 0 10px 13px -6px var(--jp-shadow-umbra-color),
        0 20px 31px 3px var(--jp-shadow-penumbra-color),
        0 8px 38px 7px var(--jp-shadow-ambient-color);
    --jp-elevation-z24: 0 11px 15px -7px var(--jp-shadow-umbra-color),
        0 24px 38px 3px var(--jp-shadow-penumbra-color),
        0 9px 46px 8px var(--jp-shadow-ambient-color);

    /* Borders
    *
    * The following variables, specify the visual styling of borders in JupyterLab.
    */

    --jp-border-width: 1px;
    --jp-border-color0: var(--md-grey-400);
    --jp-border-color1: var(--md-grey-400);
    --jp-border-color2: var(--md-grey-300);
    --jp-border-color3: var(--md-grey-200);
    --jp-inverse-border-color: var(--md-grey-600);
    --jp-border-radius: 2px;

    /* UI Fonts
    *
    * The UI font CSS variables are used for the typography all of the JupyterLab
    * user interface elements that are not directly user generated content.
    *
    * The font sizing here is done assuming that the body font size of --jp-ui-font-size1
    * is applied to a parent element. When children elements, such as headings, are sized
    * in em all things will be computed relative to that body size.
    */

    --jp-ui-font-scale-factor: 1.2;
    --jp-ui-font-size0: 0.83333em;
    --jp-ui-font-size1: 13px; /* Base font size */
    --jp-ui-font-size2: 1.2em;
    --jp-ui-font-size3: 1.44em;
    --jp-ui-font-family: system-ui, -apple-system, blinkmacsystemfont, 'Segoe UI',
        helvetica, arial, sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji',
        'Segoe UI Symbol';

    /*
    * Use these font colors against the corresponding main layout colors.
    * In a light theme, these go from dark to light.
    */

    /* Defaults use Material Design specification */
    --jp-ui-font-color0: rgba(0, 0, 0, 1);
    --jp-ui-font-color1: rgba(0, 0, 0, 0.87);
    --jp-ui-font-color2: rgba(0, 0, 0, 0.54);
    --jp-ui-font-color3: rgba(0, 0, 0, 0.38);

    /*
    * Use these against the brand/accent/warn/error colors.
    * These will typically go from light to darker, in both a dark and light theme.
    */

    --jp-ui-inverse-font-color0: rgba(255, 255, 255, 1);
    --jp-ui-inverse-font-color1: rgba(255, 255, 255, 1);
    --jp-ui-inverse-font-color2: rgba(255, 255, 255, 0.7);
    --jp-ui-inverse-font-color3: rgba(255, 255, 255, 0.5);

    /* Content Fonts
    *
    * Content font variables are used for typography of user generated content.
    *
    * The font sizing here is done assuming that the body font size of --jp-content-font-size1
    * is applied to a parent element. When children elements, such as headings, are sized
    * in em all things will be computed relative to that body size.
    */

    --jp-content-line-height: 1.6;
    --jp-content-font-scale-factor: 1.2;
    --jp-content-font-size0: 0.83333em;
    --jp-content-font-size1: 14px; /* Base font size */
    --jp-content-font-size2: 1.2em;
    --jp-content-font-size3: 1.44em;
    --jp-content-font-size4: 1.728em;
    --jp-content-font-size5: 2.0736em;

    /* This gives a magnification of about 125% in presentation mode over normal. */
    --jp-content-presentation-font-size1: 17px;
    --jp-content-heading-line-height: 1;
    --jp-content-heading-margin-top: 1.2em;
    --jp-content-heading-margin-bottom: 0.8em;
    --jp-content-heading-font-weight: 500;

    /* Defaults use Material Design specification */
    --jp-content-font-color0: rgba(0, 0, 0, 1);
    --jp-content-font-color1: rgba(0, 0, 0, 0.87);
    --jp-content-font-color2: rgba(0, 0, 0, 0.54);
    --jp-content-font-color3: rgba(0, 0, 0, 0.38);
    --jp-content-link-color: var(--md-blue-900);
    --jp-content-font-family: system-ui, -apple-system, blinkmacsystemfont,
        'Segoe UI', helvetica, arial, sans-serif, 'Apple Color Emoji',
        'Segoe UI Emoji', 'Segoe UI Symbol';

    /*
    * Code Fonts
    *
    * Code font variables are used for typography of code and other monospaces content.
    */

    --jp-code-font-size: 13px;
    --jp-code-line-height: 1.3077; /* 17px for 13px base */
    --jp-code-padding: 5px; /* 5px for 13px base, codemirror highlighting needs integer px value */
    --jp-code-font-family-default: menlo, consolas, 'DejaVu Sans Mono', monospace;
    --jp-code-font-family: var(--jp-code-font-family-default);

    /* This gives a magnification of about 125% in presentation mode over normal. */
    --jp-code-presentation-font-size: 16px;

    /* may need to tweak cursor width if you change font size */
    --jp-code-cursor-width0: 1.4px;
    --jp-code-cursor-width1: 2px;
    --jp-code-cursor-width2: 4px;

    /* Layout
    *
    * The following are the main layout colors use in JupyterLab. In a light
    * theme these would go from light to dark.
    */

    --jp-layout-color0: white;
    --jp-layout-color1: white;
    --jp-layout-color2: var(--md-grey-200);
    --jp-layout-color3: var(--md-grey-400);
    --jp-layout-color4: var(--md-grey-600);

    /* Inverse Layout
    *
    * The following are the inverse layout colors use in JupyterLab. In a light
    * theme these would go from dark to light.
    */

    --jp-inverse-layout-color0: #111;
    --jp-inverse-layout-color1: var(--md-grey-900);
    --jp-inverse-layout-color2: var(--md-grey-800);
    --jp-inverse-layout-color3: var(--md-grey-700);
    --jp-inverse-layout-color4: var(--md-grey-600);

    /* Brand/accent */

    --jp-brand-color0: var(--md-blue-900);
    --jp-brand-color1: var(--md-blue-700);
    --jp-brand-color2: var(--md-blue-300);
    --jp-brand-color3: var(--md-blue-100);
    --jp-brand-color4: var(--md-blue-50);
    --jp-accent-color0: var(--md-green-900);
    --jp-accent-color1: var(--md-green-700);
    --jp-accent-color2: var(--md-green-300);
    --jp-accent-color3: var(--md-green-100);

    /* State colors (warn, error, success, info) */

    --jp-warn-color0: var(--md-orange-900);
    --jp-warn-color1: var(--md-orange-700);
    --jp-warn-color2: var(--md-orange-300);
    --jp-warn-color3: var(--md-orange-100);
    --jp-error-color0: var(--md-red-900);
    --jp-error-color1: var(--md-red-700);
    --jp-error-color2: var(--md-red-300);
    --jp-error-color3: var(--md-red-100);
    --jp-success-color0: var(--md-green-900);
    --jp-success-color1: var(--md-green-700);
    --jp-success-color2: var(--md-green-300);
    --jp-success-color3: var(--md-green-100);
    --jp-info-color0: var(--md-cyan-900);
    --jp-info-color1: var(--md-cyan-700);
    --jp-info-color2: var(--md-cyan-300);
    --jp-info-color3: var(--md-cyan-100);

    /* Cell specific styles */

    --jp-cell-padding: 5px;
    --jp-cell-collapser-width: 8px;
    --jp-cell-collapser-min-height: 20px;
    --jp-cell-collapser-not-active-hover-opacity: 0.6;
    --jp-cell-editor-background: var(--md-grey-100);
    --jp-cell-editor-border-color: var(--md-grey-300);
    --jp-cell-editor-box-shadow: inset 0 0 2px var(--md-blue-300);
    --jp-cell-editor-active-background: var(--jp-layout-color0);
    --jp-cell-editor-active-border-color: var(--jp-brand-color1);
    --jp-cell-prompt-width: 64px;
    --jp-cell-prompt-font-family: var(--jp-code-font-family-default);
    --jp-cell-prompt-letter-spacing: 0;
    --jp-cell-prompt-opacity: 1;
    --jp-cell-prompt-not-active-opacity: 0.5;
    --jp-cell-prompt-not-active-font-color: var(--md-grey-700);

    /* A custom blend of MD grey and blue 600
    * See https://meyerweb.com/eric/tools/color-blend/#546E7A:1E88E5:5:hex */
    --jp-cell-inprompt-font-color: #307fc1;

    /* A custom blend of MD grey and orange 600
    * https://meyerweb.com/eric/tools/color-blend/#546E7A:F4511E:5:hex */
    --jp-cell-outprompt-font-color: #bf5b3d;

    /* Notebook specific styles */

    --jp-notebook-padding: 10px;
    --jp-notebook-select-background: var(--jp-layout-color1);
    --jp-notebook-multiselected-color: var(--md-blue-50);

    /* The scroll padding is calculated to fill enough space at the bottom of the
    notebook to show one single-line cell (with appropriate padding) at the top
    when the notebook is scrolled all the way to the bottom. We also subtract one
    pixel so that no scrollbar appears if we have just one single-line cell in the
    notebook. This padding is to enable a 'scroll past end' feature in a notebook.
    */
    --jp-notebook-scroll-padding: calc(
        100% - var(--jp-code-font-size) * var(--jp-code-line-height) -
        var(--jp-code-padding) - var(--jp-cell-padding) - 1px
    );

    /* Rendermime styles */

    --jp-rendermime-error-background: #fdd;
    --jp-rendermime-table-row-background: var(--md-grey-100);
    --jp-rendermime-table-row-hover-background: var(--md-light-blue-50);

    /* Dialog specific styles */

    --jp-dialog-background: rgba(0, 0, 0, 0.25);

    /* Console specific styles */

    --jp-console-padding: 10px;

    /* Toolbar specific styles */

    --jp-toolbar-border-color: var(--jp-border-color1);
    --jp-toolbar-micro-height: 8px;
    --jp-toolbar-background: var(--jp-layout-color1);
    --jp-toolbar-box-shadow: 0 0 2px 0 rgba(0, 0, 0, 0.24);
    --jp-toolbar-header-margin: 4px 4px 0 4px;
    --jp-toolbar-active-background: var(--md-grey-300);

    /* Statusbar specific styles */

    --jp-statusbar-height: 24px;

    /* Input field styles */

    --jp-input-box-shadow: inset 0 0 2px var(--md-blue-300);
    --jp-input-active-background: var(--jp-layout-color1);
    --jp-input-hover-background: var(--jp-layout-color1);
    --jp-input-background: var(--md-grey-100);
    --jp-input-border-color: var(--jp-inverse-border-color);
    --jp-input-active-border-color: var(--jp-brand-color1);
    --jp-input-active-box-shadow-color: rgba(19, 124, 189, 0.3);

    /* General editor styles */

    --jp-editor-selected-background: #d9d9d9;
    --jp-editor-selected-focused-background: #d7d4f0;
    --jp-editor-cursor-color: var(--jp-ui-font-color0);

    /* Code mirror specific styles */

    --jp-mirror-editor-keyword-color: #008000;
    --jp-mirror-editor-atom-color: #88f;
    --jp-mirror-editor-number-color: #080;
    --jp-mirror-editor-def-color: #00f;
    --jp-mirror-editor-variable-color: var(--md-grey-900);
    --jp-mirror-editor-variable-2-color: rgb(0, 54, 109);
    --jp-mirror-editor-variable-3-color: #085;
    --jp-mirror-editor-punctuation-color: #05a;
    --jp-mirror-editor-property-color: #05a;
    --jp-mirror-editor-operator-color: #a2f;
    --jp-mirror-editor-comment-color: #408080;
    --jp-mirror-editor-string-color: #ba2121;
    --jp-mirror-editor-string-2-color: #708;
    --jp-mirror-editor-meta-color: #a2f;
    --jp-mirror-editor-qualifier-color: #555;
    --jp-mirror-editor-builtin-color: #008000;
    --jp-mirror-editor-bracket-color: #997;
    --jp-mirror-editor-tag-color: #170;
    --jp-mirror-editor-attribute-color: #00c;
    --jp-mirror-editor-header-color: blue;
    --jp-mirror-editor-quote-color: #090;
    --jp-mirror-editor-link-color: #00c;
    --jp-mirror-editor-error-color: #f00;
    --jp-mirror-editor-hr-color: #999;

    /*
        RTC user specific colors.
        These colors are used for the cursor, username in the editor,
        and the icon of the user.
    */

    --jp-collaborator-color1: #ffad8e;
    --jp-collaborator-color2: #dac83d;
    --jp-collaborator-color3: #72dd76;
    --jp-collaborator-color4: #00e4d0;
    --jp-collaborator-color5: #45d4ff;
    --jp-collaborator-color6: #e2b1ff;
    --jp-collaborator-color7: #ff9de6;

    /* Vega extension styles */

    --jp-vega-background: white;

    /* Sidebar-related styles */

    --jp-sidebar-min-width: 250px;

    /* Search-related styles */

    --jp-search-toggle-off-opacity: 0.5;
    --jp-search-toggle-hover-opacity: 0.8;
    --jp-search-toggle-on-opacity: 1;
    --jp-search-selected-match-background-color: rgb(245, 200, 0);
    --jp-search-selected-match-color: black;
    --jp-search-unselected-match-background-color: var(
        --jp-inverse-layout-color0
    );
    --jp-search-unselected-match-color: var(--jp-ui-inverse-font-color0);

    /* Icon colors that work well with light or dark backgrounds */
    --jp-icon-contrast-color0: var(--md-purple-600);
    --jp-icon-contrast-color1: var(--md-green-600);
    --jp-icon-contrast-color2: var(--md-pink-600);
    --jp-icon-contrast-color3: var(--md-blue-600);

    /* Button colors */
    --jp-accept-color-normal: var(--md-blue-700);
    --jp-accept-color-hover: var(--md-blue-800);
    --jp-accept-color-active: var(--md-blue-900);
    --jp-warn-color-normal: var(--md-red-700);
    --jp-warn-color-hover: var(--md-red-800);
    --jp-warn-color-active: var(--md-red-900);
    --jp-reject-color-normal: var(--md-grey-600);
    --jp-reject-color-hover: var(--md-grey-700);
    --jp-reject-color-active: var(--md-grey-800);

    /* File or activity icons and switch semantic variables */
    --jp-jupyter-icon-color: #f37626;
    --jp-notebook-icon-color: #f37626;
    --jp-json-icon-color: var(--md-orange-700);
    --jp-console-icon-background-color: var(--md-blue-700);
    --jp-console-icon-color: white;
    --jp-terminal-icon-background-color: var(--md-grey-800);
    --jp-terminal-icon-color: var(--md-grey-200);
    --jp-text-editor-icon-color: var(--md-grey-700);
    --jp-inspector-icon-color: var(--md-grey-700);
    --jp-switch-color: var(--md-grey-400);
    --jp-switch-true-position-color: var(--md-orange-900);
    }
    </style>
    <style type="text/css">
    /* Force rendering true colors when outputing to pdf */
    * {
    -webkit-print-color-adjust: exact;
    }

    /* Misc */
    a.anchor-link {
    display: none;
    }

    /* Input area styling */
    .jp-InputArea {
    overflow: hidden;
    }

    .jp-InputArea-editor {
    overflow: hidden;
    }

    .cm-editor.cm-s-jupyter .highlight pre {
    /* weird, but --jp-code-padding defined to be 5px but 4px horizontal padding is hardcoded for pre.cm-line */
    padding: var(--jp-code-padding) 4px;
    margin: 0;

    font-family: inherit;
    font-size: inherit;
    line-height: inherit;
    color: inherit;

    }

    .jp-OutputArea-output pre {
    line-height: inherit;
    font-family: inherit;
    }

    .jp-RenderedText pre {
    color: var(--jp-content-font-color1);
    font-size: var(--jp-code-font-size);
    }

    /* Hiding the collapser by default */
    .jp-Collapser {
    display: none;
    }

    @page {
        margin: 0.5in; /* Margin for each printed piece of paper */
    }

    @media print {
    .jp-Cell-inputWrapper,
    .jp-Cell-outputWrapper {
        display: block;
    }
    }
    </style>
    <!-- Load mathjax -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/latest.js?config=TeX-AMS_CHTML-full,Safe"> </script>
    <!-- MathJax configuration -->
    <script type="text/x-mathjax-config">
        init_mathjax = function() {
            if (window.MathJax) {
            // MathJax loaded
                MathJax.Hub.Config({
                    TeX: {
                        equationNumbers: {
                        autoNumber: "AMS",
                        useLabelIds: true
                        }
                    },
                    tex2jax: {
                        inlineMath: [ ['$','$'], ["\\(","\\)"] ],
                        displayMath: [ ['$$','$$'], ["\\[","\\]"] ],
                        processEscapes: true,
                        processEnvironments: true
                    },
                    displayAlign: 'center',
                    messageStyle: 'none',
                    CommonHTML: {
                        linebreaks: {
                        automatic: true
                        }
                    }
                });

                MathJax.Hub.Queue(["Typeset", MathJax.Hub]);
            }
        }
        init_mathjax();
        </script>
    <!-- End of mathjax configuration --><script type="module">
    document.addEventListener("DOMContentLoaded", async () => {
        const diagrams = document.querySelectorAll(".jp-Mermaid > pre.mermaid");
        // do not load mermaidjs if not needed
        if (!diagrams.length) {
        return;
        }
        const mermaid = (await import("https://cdnjs.cloudflare.com/ajax/libs/mermaid/11.10.0/mermaid.esm.min.mjs")).default;
        const elkUrl = "https://cdnjs.cloudflare.com/ajax/libs/mermaid-layout-elk/0.1.9/mermaid-layout-elk.esm.min.mjs";
        if(elkUrl) {
        const elkLayouts = (await import(elkUrl)).default;
        mermaid.registerLayoutLoaders(elkLayouts);
        }
        const parser = new DOMParser();

        mermaid.initialize({
        maxTextSize: 100000,
        maxEdges: 100000,
        startOnLoad: false,
        fontFamily: window
            .getComputedStyle(document.body)
            .getPropertyValue("--jp-ui-font-family"),
        theme: document.querySelector("body[data-jp-theme-light='true']")
            ? "default"
            : "dark",
        });

        let _nextMermaidId = 0;

        function makeMermaidImage(svg) {
        const img = document.createElement("img");
        const doc = parser.parseFromString(svg, "image/svg+xml");
        const svgEl = doc.querySelector("svg");
        const { maxWidth } = svgEl?.style || {};
        const firstTitle = doc.querySelector("title");
        const firstDesc = doc.querySelector("desc");

        img.setAttribute("src", `data:image/svg+xml,${encodeURIComponent(svg)}`);
        if (maxWidth) {
            img.width = parseInt(maxWidth);
        }
        if (firstTitle) {
            img.setAttribute("alt", firstTitle.textContent);
        }
        if (firstDesc) {
            const caption = document.createElement("figcaption");
            caption.className = "sr-only";
            caption.textContent = firstDesc.textContent;
            return [img, caption];
        }
        return [img];
        }

        async function makeMermaidError(text) {
        let errorMessage = "";
        try {
            await mermaid.parse(text);
        } catch (err) {
            errorMessage = `${err}`;
        }

        const result = document.createElement("details");
        result.className = 'jp-RenderedMermaid-Details';
        const summary = document.createElement("summary");
        summary.className = 'jp-RenderedMermaid-Summary';
        const pre = document.createElement("pre");
        const code = document.createElement("code");
        code.innerText = text;
        pre.appendChild(code);
        summary.appendChild(pre);
        result.appendChild(summary);

        const warning = document.createElement("pre");
        warning.innerText = errorMessage;
        result.appendChild(warning);
        return [result];
        }

        async function renderOneMarmaid(src) {
        const id = `jp-mermaid-${_nextMermaidId++}`;
        const parent = src.parentNode;
        let raw = src.textContent.trim();
        const el = document.createElement("div");
        el.style.visibility = "hidden";
        document.body.appendChild(el);
        let results = null;
        let output = null;
        try {
            let { svg } = await mermaid.render(id, raw, el);
            svg = cleanMermaidSvg(svg);
            results = makeMermaidImage(svg);
            output = document.createElement("figure");
            results.map(output.appendChild, output);
        } catch (err) {
            parent.classList.add("jp-mod-warning");
            results = await makeMermaidError(raw);
            output = results[0];
        } finally {
            el.remove();
        }
        parent.classList.add("jp-RenderedMermaid");
        parent.appendChild(output);
        }


        /**
        * Post-process to ensure mermaid diagrams contain only valid SVG and XHTML.
        */
        function cleanMermaidSvg(svg) {
        svg = svg.replace(RE_VOID_ELEMENT, replaceVoidElement);
        return `${SVG_XML_HEADER}${svg}`;
        }


        /**
        * A regular expression for all void elements, which may include attributes and
        * a slash.
        *
        * @see https://developer.mozilla.org/en-US/docs/Glossary/Void_element
        *
        * Of these, only `<br>` is generated by Mermaid in place of `\n`,
        * but _any_ "malformed" tag will break the SVG rendering entirely.
        */
        const RE_VOID_ELEMENT =
        /<\s*(area|base|br|col|embed|hr|img|input|link|meta|param|source|track|wbr)\s*([^>]*?)\s*>/gi;

        /**
        * Ensure a void element is closed with a slash, preserving any attributes.
        */
        function replaceVoidElement(match, tag, rest) {
        rest = rest.trim();
        if (!rest.endsWith('/')) {
            rest = `${rest} /`;
        }
        return `<${tag} ${rest}>`;
        }


    /**
    * Named HTML entities with their decimal equivalent codes.
    *
    * @see https://www.w3.org/TR/WD-html40-970708/sgml/entities.html
    * */
    const HTML_ENTITIES = `<!ENTITY Aacute "&#193;">
    <!ENTITY aacute "&#225;">
    <!ENTITY Acirc "&#194;">
    <!ENTITY acirc "&#226;">
    <!ENTITY acute "&#180;">
    <!ENTITY AElig "&#198;">
    <!ENTITY aelig "&#230;">
    <!ENTITY Agrave "&#192;">
    <!ENTITY agrave "&#224;">
    <!ENTITY alefsym "&#8501;">
    <!ENTITY Alpha "&#913;">
    <!ENTITY alpha "&#945;">
    <!ENTITY amp "&#38;">
    <!ENTITY and "&#8869;">
    <!ENTITY ang "&#8736;">
    <!ENTITY Aring "&#197;">
    <!ENTITY aring "&#229;">
    <!ENTITY asymp "&#8776;">
    <!ENTITY Atilde "&#195;">
    <!ENTITY atilde "&#227;">
    <!ENTITY Auml "&#196;">
    <!ENTITY auml "&#228;">
    <!ENTITY bdquo "&#8222;">
    <!ENTITY Beta "&#914;">
    <!ENTITY beta "&#946;">
    <!ENTITY brvbar "&#166;">
    <!ENTITY bull "&#8226;">
    <!ENTITY cap "&#8745;">
    <!ENTITY Ccedil "&#199;">
    <!ENTITY ccedil "&#231;">
    <!ENTITY cedil "&#184;">
    <!ENTITY cent "&#162;">
    <!ENTITY Chi "&#935;">
    <!ENTITY chi "&#967;">
    <!ENTITY circ "&#710;">
    <!ENTITY clubs "&#9827;">
    <!ENTITY cong "&#8773;">
    <!ENTITY copy "&#169;">
    <!ENTITY crarr "&#8629;">
    <!ENTITY cup "&#8746;">
    <!ENTITY curren "&#164;">
    <!ENTITY dagger "&#8224;">
    <!ENTITY Dagger "&#8225;">
    <!ENTITY darr "&#8595;">
    <!ENTITY dArr "&#8659;">
    <!ENTITY deg "&#176;">
    <!ENTITY Delta "&#916;">
    <!ENTITY delta "&#948;">
    <!ENTITY diams "&#9830;">
    <!ENTITY divide "&#247;">
    <!ENTITY Eacute "&#201;">
    <!ENTITY eacute "&#233;">
    <!ENTITY Ecirc "&#202;">
    <!ENTITY ecirc "&#234;">
    <!ENTITY Egrave "&#200;">
    <!ENTITY egrave "&#232;">
    <!ENTITY empty "&#8709;">
    <!ENTITY emsp "&#8195;">
    <!ENTITY ensp "&#8194;">
    <!ENTITY epsilon "&#949;">
    <!ENTITY Epsilon "&#917;">
    <!ENTITY equiv "&#8801;">
    <!ENTITY Eta "&#919;">
    <!ENTITY eta "&#951;">
    <!ENTITY ETH "&#208;">
    <!ENTITY eth "&#240;">
    <!ENTITY Euml "&#203;">
    <!ENTITY euml "&#235;">
    <!ENTITY exist "&#8707;">
    <!ENTITY fnof "&#402;">
    <!ENTITY forall "&#8704;">
    <!ENTITY frac12 "&#189;">
    <!ENTITY frac14 "&#188;">
    <!ENTITY frac34 "&#190;">
    <!ENTITY frasl "&#8260;">
    <!ENTITY Gamma "&#915;">
    <!ENTITY gamma "&#947;">
    <!ENTITY ge "&#8805;">
    <!ENTITY gt "&#62;">
    <!ENTITY harr "&#8596;">
    <!ENTITY hArr "&#8660;">
    <!ENTITY hearts "&#9829;">
    <!ENTITY hellip "&#8230;">
    <!ENTITY Iacute "&#205;">
    <!ENTITY iacute "&#237;">
    <!ENTITY Icirc "&#206;">
    <!ENTITY icirc "&#238;">
    <!ENTITY iexcl "&#161;">
    <!ENTITY Igrave "&#204;">
    <!ENTITY igrave "&#236;">
    <!ENTITY image "&#8465;">
    <!ENTITY infin "&#8734;">
    <!ENTITY int "&#8747;">
    <!ENTITY Iota "&#921;">
    <!ENTITY iota "&#953;">
    <!ENTITY iquest "&#191;">
    <!ENTITY isin "&#8712;">
    <!ENTITY Iuml "&#207;">
    <!ENTITY iuml "&#239;">
    <!ENTITY Kappa "&#922;">
    <!ENTITY kappa "&#954;">
    <!ENTITY Lambda "&#923;">
    <!ENTITY lambda "&#955;">
    <!ENTITY lang "&#9001;">
    <!ENTITY laquo "&#171;">
    <!ENTITY larr "&#8592;">
    <!ENTITY lArr "&#8656;">
    <!ENTITY lceil "&#8968;">
    <!ENTITY ldquo "&#8220;">
    <!ENTITY le "&#8804;">
    <!ENTITY lfloor "&#8970;">
    <!ENTITY lowast "&#8727;">
    <!ENTITY loz "&#9674;">
    <!ENTITY lrm "&#8206;">
    <!ENTITY lsaquo "&#8249;">
    <!ENTITY lsquo "&#8216;">
    <!ENTITY lt "&#60;">
    <!ENTITY macr "&#175;">
    <!ENTITY mdash "&#8212;">
    <!ENTITY micro "&#181;">
    <!ENTITY middot "&#183;">
    <!ENTITY minus "&#8722;">
    <!ENTITY Mu "&#924;">
    <!ENTITY mu "&#956;">
    <!ENTITY nabla "&#8711;">
    <!ENTITY nbsp "&#160;">
    <!ENTITY ndash "&#8211;">
    <!ENTITY ne "&#8800;">
    <!ENTITY ni "&#8715;">
    <!ENTITY not "&#172;">
    <!ENTITY notin "&#8713;">
    <!ENTITY nsub "&#8836;">
    <!ENTITY Ntilde "&#209;">
    <!ENTITY ntilde "&#241;">
    <!ENTITY Nu "&#925;">
    <!ENTITY nu "&#957;">
    <!ENTITY Oacute "&#211;">
    <!ENTITY oacute "&#243;">
    <!ENTITY Ocirc "&#212;">
    <!ENTITY ocirc "&#244;">
    <!ENTITY OElig "&#338;">
    <!ENTITY oelig "&#339;">
    <!ENTITY Ograve "&#210;">
    <!ENTITY ograve "&#242;">
    <!ENTITY oline "&#8254;">
    <!ENTITY Omega "&#937;">
    <!ENTITY omega "&#969;">
    <!ENTITY Omicron "&#927;">
    <!ENTITY omicron "&#959;">
    <!ENTITY oplus "&#8853;">
    <!ENTITY or "&#8870;">
    <!ENTITY ordf "&#170;">
    <!ENTITY ordm "&#186;">
    <!ENTITY Oslash "&#216;">
    <!ENTITY oslash "&#248;">
    <!ENTITY Otilde "&#213;">
    <!ENTITY otilde "&#245;">
    <!ENTITY otimes "&#8855;">
    <!ENTITY Ouml "&#214;">
    <!ENTITY ouml "&#246;">
    <!ENTITY para "&#182;">
    <!ENTITY part "&#8706;">
    <!ENTITY permil "&#8240;">
    <!ENTITY perp "&#8869;">
    <!ENTITY Phi "&#934;">
    <!ENTITY phi "&#966;">
    <!ENTITY Pi "&#928;">
    <!ENTITY pi "&#960;">
    <!ENTITY piv "&#982;">
    <!ENTITY plusmn "&#177;">
    <!ENTITY pound "&#163;">
    <!ENTITY prime "&#8242;">
    <!ENTITY Prime "&#8243;">
    <!ENTITY prod "&#8719;">
    <!ENTITY prop "&#8733;">
    <!ENTITY Psi "&#936;">
    <!ENTITY psi "&#968;">
    <!ENTITY quot "&#34;">
    <!ENTITY radic "&#8730;">
    <!ENTITY rang "&#9002;">
    <!ENTITY raquo "&#187;">
    <!ENTITY rarr "&#8594;">
    <!ENTITY rArr "&#8658;">
    <!ENTITY rceil "&#8969;">
    <!ENTITY rdquo "&#8221;">
    <!ENTITY real "&#8476;">
    <!ENTITY reg "&#174;">
    <!ENTITY rfloor "&#8971;">
    <!ENTITY Rho "&#929;">
    <!ENTITY rho "&#961;">
    <!ENTITY rlm "&#8207;">
    <!ENTITY rsaquo "&#8250;">
    <!ENTITY rsquo "&#8217;">
    <!ENTITY sbquo "&#8218;">
    <!ENTITY Scaron "&#352;">
    <!ENTITY scaron "&#353;">
    <!ENTITY sdot "&#8901;">
    <!ENTITY sect "&#167;">
    <!ENTITY shy "&#173;">
    <!ENTITY Sigma "&#931;">
    <!ENTITY sigma "&#963;">
    <!ENTITY sigmaf "&#962;">
    <!ENTITY sim "&#8764;">
    <!ENTITY spades "&#9824;">
    <!ENTITY sub "&#8834;">
    <!ENTITY sube "&#8838;">
    <!ENTITY sum "&#8721;">
    <!ENTITY sup "&#8835;">
    <!ENTITY sup1 "&#185;">
    <!ENTITY sup2 "&#178;">
    <!ENTITY sup3 "&#179;">
    <!ENTITY supe "&#8839;">
    <!ENTITY szlig "&#223;">
    <!ENTITY Tau "&#932;">
    <!ENTITY tau "&#964;">
    <!ENTITY there4 "&#8756;">
    <!ENTITY Theta "&#920;">
    <!ENTITY theta "&#952;">
    <!ENTITY thetasym "&#977;">
    <!ENTITY thinsp "&#8201;">
    <!ENTITY THORN "&#222;">
    <!ENTITY thorn "&#254;">
    <!ENTITY tilde "&#732;">
    <!ENTITY times "&#215;">
    <!ENTITY trade "&#8482;">
    <!ENTITY Uacute "&#218;">
    <!ENTITY uacute "&#250;">
    <!ENTITY uarr "&#8593;">
    <!ENTITY uArr "&#8657;">
    <!ENTITY Ucirc "&#219;">
    <!ENTITY ucirc "&#251;">
    <!ENTITY Ugrave "&#217;">
    <!ENTITY ugrave "&#249;">
    <!ENTITY uml "&#168;">
    <!ENTITY upsih "&#978;">
    <!ENTITY Upsilon "&#933;">
    <!ENTITY upsilon "&#965;">
    <!ENTITY Uuml "&#220;">
    <!ENTITY uuml "&#252;">
    <!ENTITY weierp "&#8472;">
    <!ENTITY Xi "&#926;">
    <!ENTITY xi "&#958;">
    <!ENTITY Yacute "&#221;">
    <!ENTITY yacute "&#253;">
    <!ENTITY yen "&#165;">
    <!ENTITY Yuml "&#376;">
    <!ENTITY yuml "&#255;">
    <!ENTITY Zeta "&#918;">
    <!ENTITY zeta "&#950;">
    <!ENTITY zwj "&#8205;">
    <!ENTITY zwnj "&#8204;">`.replace(/\n/g, ' ');

    /**
    * A reasonably strict xml declaration.
    */
    const XML_DECL = '<?xml version="1.0" standalone="no"?>';

    /**
    * The beginning of the XML doctype declaration.
    */
    const DOCTYPE_START = `<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" "http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd" [`;

    /**
    * The end of the XML docype declaration.
    */
    const DOCTYPE_END = ']>';

    /**
    * A full header for an SVG XML document.
    */
    const SVG_XML_HEADER = `${XML_DECL}
        ${DOCTYPE_START}${HTML_ENTITIES}${DOCTYPE_END}`;

        void Promise.all([...diagrams].map(renderOneMarmaid));
    });
    </script>
    <style>
    .jp-Mermaid:not(.jp-RenderedMermaid) {
        display: none;
    }

    .jp-RenderedMermaid {
        overflow: auto;
        display: flex;
    }

    .jp-RenderedMermaid.jp-mod-warning {
        width: auto;
        padding: 0.5em;
        margin-top: 0.5em;
        border: var(--jp-border-width) solid var(--jp-warn-color2);
        border-radius: var(--jp-border-radius);
        color: var(--jp-ui-font-color1);
        font-size: var(--jp-ui-font-size1);
        white-space: pre-wrap;
        word-wrap: break-word;
    }

    .jp-RenderedMermaid figure {
        margin: 0;
        overflow: auto;
        max-width: 100%;
    }

    .jp-RenderedMermaid img {
        max-width: 100%;
    }

    .jp-RenderedMermaid-Details > pre {
        margin-top: 1em;
    }

    .jp-RenderedMermaid-Summary {
        color: var(--jp-warn-color2);
    }

    .jp-RenderedMermaid:not(.jp-mod-warning) pre {
        display: none;
    }

    .jp-RenderedMermaid-Summary > pre {
        display: inline-block;
        white-space: normal;
    }
    </style>
    <!-- End of mermaid configuration --></head>
    <body class="jp-Notebook" data-jp-theme-light="true" data-jp-theme-name="JupyterLab Light">
    <main>
    <div class="jp-Cell jp-MarkdownCell jp-Notebook-cell" id="cell-id=98e5d2eb">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
    </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
    <h1 id="Data-Preprocessing-and-EDA-for-E%E2%80%91Commerce-Orders">Data Preprocessing and EDA for E‑Commerce Orders<a class="anchor-link" href="#Data-Preprocessing-and-EDA-for-E%E2%80%91Commerce-Orders">¶</a></h1><p>Objective of this section will be to load four core tables (orders, order_items, order_shipping, and payments) which contain the raw transactional and logistical details of the business. Once the data is consolidated, we will perform rigorous cleaning and transformation to resolve inconsistencies and prepare the features for modeling. Finally, we will conduct an Exploratory Data Analysis (EDA) to visualize key trends, allowing us to uncover the underlying patterns in order behavior and logistics performance that will drive our subsequent machine learning tasks.</p>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell jp-MarkdownCell jp-Notebook-cell" id="cell-id=e6c7588d">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
    </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
    <h2 id="Setup">Setup<a class="anchor-link" href="#Setup">¶</a></h2><p>Run the cell below to import the required Python packages.</p>
    </div>
    </div>
    </div>
    </div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs" id="cell-id=6c11bc76">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea">
    <div class="jp-InputPrompt jp-InputArea-prompt">In [2]:</div>
    <div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
    <div class="cm-editor cm-s-jupyter">
    <div class="highlight hl-python"><pre><span></span><span class="kn">import</span><span class="w"> </span><span class="nn">numpy</span><span class="w"> </span><span class="k">as</span><span class="w"> </span><span class="nn">np</span>
    <span class="kn">import</span><span class="w"> </span><span class="nn">pandas</span><span class="w"> </span><span class="k">as</span><span class="w"> </span><span class="nn">pd</span>
    <span class="kn">import</span><span class="w"> </span><span class="nn">matplotlib.pyplot</span><span class="w"> </span><span class="k">as</span><span class="w"> </span><span class="nn">plt</span>
    <span class="kn">import</span><span class="w"> </span><span class="nn">sklearn</span>
    <span class="kn">import</span><span class="w"> </span><span class="nn">seaborn</span><span class="w"> </span><span class="k">as</span><span class="w"> </span><span class="nn">sns</span>

    <span class="n">plt</span><span class="o">.</span><span class="n">style</span><span class="o">.</span><span class="n">use</span><span class="p">(</span><span class="s1">'seaborn-v0_8'</span><span class="p">)</span>
    </pre></div>
    </div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell jp-MarkdownCell jp-Notebook-cell" id="cell-id=80307a84">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
    </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
    <hr/>
    <h2 id="Part-1:-Data-Preprocessing">Part 1: Data Preprocessing<a class="anchor-link" href="#Part-1:-Data-Preprocessing">¶</a></h2><h3 id="1.1-Data-Loading-&amp;-Joining">1.1 Data Loading &amp; Joining<a class="anchor-link" href="#1.1-Data-Loading-&amp;-Joining">¶</a></h3><p>We first load each table, inspect it, and then join them into a single DataFrame.</p>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell jp-MarkdownCell jp-Notebook-cell" id="cell-id=edbe5ac1">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
    </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
    <h4 id="Load-the-CSV-files">Load the CSV files<a class="anchor-link" href="#Load-the-CSV-files">¶</a></h4><p>In this initial phase, the data foundation is established by ingesting the raw relational datasets. Specifically df_orders, df_order_items, df_shipping, and df_payments. We perform this step to ensure that all core business entities are correctly mapped into our analytical environment, providing a reliable starting point before we move into the integration and transformation stages.</p>
    </div>
    </div>
    </div>
    </div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs" id="cell-id=1569a5bf">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea">
    <div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
    <div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
    <div class="cm-editor cm-s-jupyter">
    <div class="highlight hl-python"><pre><span></span><span class="c1"># Load the CSV files</span>
    <span class="n">df_order_items</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s1">'order_items.csv'</span><span class="p">)</span>
    <span class="n">df_shipping</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s1">'order_shipping.csv'</span><span class="p">)</span>
    <span class="n">df_orders</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s1">'orders.csv'</span><span class="p">)</span>
    <span class="n">df_payments</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s1">'payments.csv'</span><span class="p">)</span>
    </pre></div>
    </div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell jp-MarkdownCell jp-Notebook-cell" id="cell-id=0e6cccfc">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
    </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
    <h4 id="Inspect-each-table">Inspect each table<a class="anchor-link" href="#Inspect-each-table">¶</a></h4><p>By examining the initial records and dimensional shapes, the underlying relational schema is validated, ensuring a clear understanding of the data grain before proceeding to integration.</p>
    </div>
    </div>
    </div>
    </div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=10d30142">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea">
    <div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
    <div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
    <div class="cm-editor cm-s-jupyter">
    <div class="highlight hl-python"><pre><span></span><span class="c1"># Execute structural audit for all primary dataframes</span>
    <span class="n">display</span><span class="p">(</span><span class="n">df_order_items</span><span class="o">.</span><span class="n">head</span><span class="p">())</span>
    <span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s2">"Shape of order_items: </span><span class="si">{</span><span class="n">df_order_items</span><span class="o">.</span><span class="n">shape</span><span class="si">}</span><span class="s2">"</span><span class="p">)</span>

    <span class="n">display</span><span class="p">(</span><span class="n">df_shipping</span><span class="o">.</span><span class="n">head</span><span class="p">())</span>
    <span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s2">"Shape of order_shipping: </span><span class="si">{</span><span class="n">df_shipping</span><span class="o">.</span><span class="n">shape</span><span class="si">}</span><span class="s2">"</span><span class="p">)</span>

    <span class="n">display</span><span class="p">(</span><span class="n">df_orders</span><span class="o">.</span><span class="n">head</span><span class="p">())</span>
    <span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s2">"Shape of orders: </span><span class="si">{</span><span class="n">df_orders</span><span class="o">.</span><span class="n">shape</span><span class="si">}</span><span class="s2">"</span><span class="p">)</span>

    <span class="n">display</span><span class="p">(</span><span class="n">df_payments</span><span class="o">.</span><span class="n">head</span><span class="p">())</span>
    <span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s2">"Shape of payments: </span><span class="si">{</span><span class="n">df_payments</span><span class="o">.</span><span class="n">shape</span><span class="si">}</span><span class="s2">"</span><span class="p">)</span>
    </pre></div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell-outputWrapper">
    <div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
    </div>
    <div class="jp-OutputArea jp-Cell-outputArea">
    <div class="jp-OutputArea-child">
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
    <div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output" data-mime-type="text/html" tabindex="0">
    <div class="colab-df-container" id="df-b9427683-c339-4c1a-92d3-a909d1962e4b">
    <div>
    <style scoped="">
        .dataframe tbody tr th:only-of-type {
            vertical-align: middle;
        }

        .dataframe tbody tr th {
            vertical-align: top;
        }

        .dataframe thead th {
            text-align: right;
        }
    </style>
    <table border="1" class="dataframe">
    <thead>
    <tr style="text-align: right;">
    <th></th>
    <th>order_id</th>
    <th>num_items</th>
    <th>num_unique_products</th>
    <th>num_unique_sellers</th>
    <th>total_item_price</th>
    <th>avg_item_price</th>
    <th>total_freight_value</th>
    <th>top_product_category</th>
    </tr>
    </thead>
    <tbody>
    <tr>
    <th>0</th>
    <td>sdv-id-whzjUX</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>352.420029</td>
    <td>369.966521</td>
    <td>68.790159</td>
    <td>construction_tools_construction</td>
    </tr>
    <tr>
    <th>1</th>
    <td>sdv-id-gqShVM</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>1580.187928</td>
    <td>1089.284136</td>
    <td>84.603289</td>
    <td>auto</td>
    </tr>
    <tr>
    <th>2</th>
    <td>sdv-id-vtaqcY</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>45.969263</td>
    <td>36.969754</td>
    <td>24.022637</td>
    <td>furniture_decor</td>
    </tr>
    <tr>
    <th>3</th>
    <td>sdv-id-xkqwdo</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>146.023435</td>
    <td>126.755360</td>
    <td>16.945349</td>
    <td>consoles_games</td>
    </tr>
    <tr>
    <th>4</th>
    <td>sdv-id-sGyHvQ</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>30.525812</td>
    <td>22.797409</td>
    <td>17.785846</td>
    <td>air_conditioning</td>
    </tr>
    </tbody>
    </table>
    </div>
    <div class="colab-df-buttons">
    <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-b9427683-c339-4c1a-92d3-a909d1962e4b')" style="display:none;" title="Convert this dataframe to an interactive table.">
    <svg height="24px" viewbox="0 -960 960 960" xmlns="http://www.w3.org/2000/svg">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"></path>
    </svg>
    </button>
    <style>
        .colab-df-container {
        display:flex;
        gap: 12px;
        }

        .colab-df-convert {
        background-color: #E8F0FE;
        border: none;
        border-radius: 50%;
        cursor: pointer;
        display: none;
        fill: #1967D2;
        height: 32px;
        padding: 0 0 0 0;
        width: 32px;
        }

        .colab-df-convert:hover {
        background-color: #E2EBFA;
        box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
        fill: #174EA6;
        }

        .colab-df-buttons div {
        margin-bottom: 4px;
        }

        [theme=dark] .colab-df-convert {
        background-color: #3B4455;
        fill: #D2E3FC;
        }

        [theme=dark] .colab-df-convert:hover {
        background-color: #434B5C;
        box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
        filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
        fill: #FFFFFF;
        }
    </style>
    <script>
        const buttonEl =
            document.querySelector('#df-b9427683-c339-4c1a-92d3-a909d1962e4b button.colab-df-convert');
        buttonEl.style.display =
            google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
            const element = document.querySelector('#df-b9427683-c339-4c1a-92d3-a909d1962e4b');
            const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                        [key], {});
            if (!dataTable) return;

            const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
            element.innerHTML = '';
            dataTable['output_type'] = 'display_data';
            await google.colab.output.renderOutput(dataTable, element);
            const docLink = document.createElement('div');
            docLink.innerHTML = docLinkHtml;
            element.appendChild(docLink);
        }
        </script>
    </div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-OutputArea-child">
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
    <div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain" tabindex="0">
    <pre>Shape of order_items: (100000, 8)
    </pre>
    </div>
    </div>
    <div class="jp-OutputArea-child">
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
    <div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output" data-mime-type="text/html" tabindex="0">
    <div class="colab-df-container" id="df-ecc5a64a-dc87-4e50-a0de-fc9d434d7164">
    <div>
    <style scoped="">
        .dataframe tbody tr th:only-of-type {
            vertical-align: middle;
        }

        .dataframe tbody tr th {
            vertical-align: top;
        }

        .dataframe thead th {
            text-align: right;
        }
    </style>
    <table border="1" class="dataframe">
    <thead>
    <tr style="text-align: right;">
    <th></th>
    <th>order_id</th>
    <th>customer_state</th>
    </tr>
    </thead>
    <tbody>
    <tr>
    <th>0</th>
    <td>sdv-id-whzjUX</td>
    <td>Massachusetts</td>
    </tr>
    <tr>
    <th>1</th>
    <td>sdv-id-gqShVM</td>
    <td>Ohio</td>
    </tr>
    <tr>
    <th>2</th>
    <td>sdv-id-vtaqcY</td>
    <td>Wisconsin</td>
    </tr>
    <tr>
    <th>3</th>
    <td>sdv-id-xkqwdo</td>
    <td>Michigan</td>
    </tr>
    <tr>
    <th>4</th>
    <td>sdv-id-sGyHvQ</td>
    <td>Nevada</td>
    </tr>
    </tbody>
    </table>
    </div>
    <div class="colab-df-buttons">
    <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-ecc5a64a-dc87-4e50-a0de-fc9d434d7164')" style="display:none;" title="Convert this dataframe to an interactive table.">
    <svg height="24px" viewbox="0 -960 960 960" xmlns="http://www.w3.org/2000/svg">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"></path>
    </svg>
    </button>
    <style>
        .colab-df-container {
        display:flex;
        gap: 12px;
        }

        .colab-df-convert {
        background-color: #E8F0FE;
        border: none;
        border-radius: 50%;
        cursor: pointer;
        display: none;
        fill: #1967D2;
        height: 32px;
        padding: 0 0 0 0;
        width: 32px;
        }

        .colab-df-convert:hover {
        background-color: #E2EBFA;
        box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
        fill: #174EA6;
        }

        .colab-df-buttons div {
        margin-bottom: 4px;
        }

        [theme=dark] .colab-df-convert {
        background-color: #3B4455;
        fill: #D2E3FC;
        }

        [theme=dark] .colab-df-convert:hover {
        background-color: #434B5C;
        box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
        filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
        fill: #FFFFFF;
        }
    </style>
    <script>
        const buttonEl =
            document.querySelector('#df-ecc5a64a-dc87-4e50-a0de-fc9d434d7164 button.colab-df-convert');
        buttonEl.style.display =
            google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
            const element = document.querySelector('#df-ecc5a64a-dc87-4e50-a0de-fc9d434d7164');
            const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                        [key], {});
            if (!dataTable) return;

            const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
            element.innerHTML = '';
            dataTable['output_type'] = 'display_data';
            await google.colab.output.renderOutput(dataTable, element);
            const docLink = document.createElement('div');
            docLink.innerHTML = docLinkHtml;
            element.appendChild(docLink);
        }
        </script>
    </div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-OutputArea-child">
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
    <div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain" tabindex="0">
    <pre>Shape of order_shipping: (100000, 2)
    </pre>
    </div>
    </div>
    <div class="jp-OutputArea-child">
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
    <div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output" data-mime-type="text/html" tabindex="0">
    <div class="colab-df-container" id="df-45462419-ed1c-4dc6-a8fb-cd9ef28bda94">
    <div>
    <style scoped="">
        .dataframe tbody tr th:only-of-type {
            vertical-align: middle;
        }

        .dataframe tbody tr th {
            vertical-align: top;
        }

        .dataframe thead th {
            text-align: right;
        }
    </style>
    <table border="1" class="dataframe">
    <thead>
    <tr style="text-align: right;">
    <th></th>
    <th>order_id</th>
    <th>order_status</th>
    <th>order_purchase_hour</th>
    <th>order_purchase_dayofweek</th>
    <th>order_purchase_month</th>
    <th>order_total_value</th>
    </tr>
    </thead>
    <tbody>
    <tr>
    <th>0</th>
    <td>sdv-id-whzjUX</td>
    <td>shipped</td>
    <td>10</td>
    <td>4</td>
    <td>4</td>
    <td>744.312535</td>
    </tr>
    <tr>
    <th>1</th>
    <td>sdv-id-gqShVM</td>
    <td>delivered</td>
    <td>19</td>
    <td>2</td>
    <td>4</td>
    <td>1030.521912</td>
    </tr>
    <tr>
    <th>2</th>
    <td>sdv-id-vtaqcY</td>
    <td>delivered</td>
    <td>18</td>
    <td>4</td>
    <td>8</td>
    <td>28.472994</td>
    </tr>
    <tr>
    <th>3</th>
    <td>sdv-id-xkqwdo</td>
    <td>invoiced</td>
    <td>23</td>
    <td>1</td>
    <td>8</td>
    <td>143.914263</td>
    </tr>
    <tr>
    <th>4</th>
    <td>sdv-id-sGyHvQ</td>
    <td>delivered</td>
    <td>19</td>
    <td>0</td>
    <td>2</td>
    <td>16.944537</td>
    </tr>
    </tbody>
    </table>
    </div>
    <div class="colab-df-buttons">
    <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-45462419-ed1c-4dc6-a8fb-cd9ef28bda94')" style="display:none;" title="Convert this dataframe to an interactive table.">
    <svg height="24px" viewbox="0 -960 960 960" xmlns="http://www.w3.org/2000/svg">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"></path>
    </svg>
    </button>
    <style>
        .colab-df-container {
        display:flex;
        gap: 12px;
        }

        .colab-df-convert {
        background-color: #E8F0FE;
        border: none;
        border-radius: 50%;
        cursor: pointer;
        display: none;
        fill: #1967D2;
        height: 32px;
        padding: 0 0 0 0;
        width: 32px;
        }

        .colab-df-convert:hover {
        background-color: #E2EBFA;
        box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
        fill: #174EA6;
        }

        .colab-df-buttons div {
        margin-bottom: 4px;
        }

        [theme=dark] .colab-df-convert {
        background-color: #3B4455;
        fill: #D2E3FC;
        }

        [theme=dark] .colab-df-convert:hover {
        background-color: #434B5C;
        box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
        filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
        fill: #FFFFFF;
        }
    </style>
    <script>
        const buttonEl =
            document.querySelector('#df-45462419-ed1c-4dc6-a8fb-cd9ef28bda94 button.colab-df-convert');
        buttonEl.style.display =
            google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
            const element = document.querySelector('#df-45462419-ed1c-4dc6-a8fb-cd9ef28bda94');
            const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                        [key], {});
            if (!dataTable) return;

            const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
            element.innerHTML = '';
            dataTable['output_type'] = 'display_data';
            await google.colab.output.renderOutput(dataTable, element);
            const docLink = document.createElement('div');
            docLink.innerHTML = docLinkHtml;
            element.appendChild(docLink);
        }
        </script>
    </div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-OutputArea-child">
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
    <div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain" tabindex="0">
    <pre>Shape of orders: (100000, 6)
    </pre>
    </div>
    </div>
    <div class="jp-OutputArea-child">
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
    <div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output" data-mime-type="text/html" tabindex="0">
    <div class="colab-df-container" id="df-002e65d1-fe55-45f8-b146-f8d0858c8519">
    <div>
    <style scoped="">
        .dataframe tbody tr th:only-of-type {
            vertical-align: middle;
        }

        .dataframe tbody tr th {
            vertical-align: top;
        }

        .dataframe thead th {
            text-align: right;
        }
    </style>
    <table border="1" class="dataframe">
    <thead>
    <tr style="text-align: right;">
    <th></th>
    <th>order_id</th>
    <th>payment_type</th>
    </tr>
    </thead>
    <tbody>
    <tr>
    <th>0</th>
    <td>sdv-id-whzjUX</td>
    <td>voucher</td>
    </tr>
    <tr>
    <th>1</th>
    <td>sdv-id-gqShVM</td>
    <td>voucher</td>
    </tr>
    <tr>
    <th>2</th>
    <td>sdv-id-vtaqcY</td>
    <td>voucher</td>
    </tr>
    <tr>
    <th>3</th>
    <td>sdv-id-xkqwdo</td>
    <td>credit_card</td>
    </tr>
    <tr>
    <th>4</th>
    <td>sdv-id-sGyHvQ</td>
    <td>credit_card</td>
    </tr>
    </tbody>
    </table>
    </div>
    <div class="colab-df-buttons">
    <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-002e65d1-fe55-45f8-b146-f8d0858c8519')" style="display:none;" title="Convert this dataframe to an interactive table.">
    <svg height="24px" viewbox="0 -960 960 960" xmlns="http://www.w3.org/2000/svg">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"></path>
    </svg>
    </button>
    <style>
        .colab-df-container {
        display:flex;
        gap: 12px;
        }

        .colab-df-convert {
        background-color: #E8F0FE;
        border: none;
        border-radius: 50%;
        cursor: pointer;
        display: none;
        fill: #1967D2;
        height: 32px;
        padding: 0 0 0 0;
        width: 32px;
        }

        .colab-df-convert:hover {
        background-color: #E2EBFA;
        box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
        fill: #174EA6;
        }

        .colab-df-buttons div {
        margin-bottom: 4px;
        }

        [theme=dark] .colab-df-convert {
        background-color: #3B4455;
        fill: #D2E3FC;
        }

        [theme=dark] .colab-df-convert:hover {
        background-color: #434B5C;
        box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
        filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
        fill: #FFFFFF;
        }
    </style>
    <script>
        const buttonEl =
            document.querySelector('#df-002e65d1-fe55-45f8-b146-f8d0858c8519 button.colab-df-convert');
        buttonEl.style.display =
            google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
            const element = document.querySelector('#df-002e65d1-fe55-45f8-b146-f8d0858c8519');
            const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                        [key], {});
            if (!dataTable) return;

            const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
            element.innerHTML = '';
            dataTable['output_type'] = 'display_data';
            await google.colab.output.renderOutput(dataTable, element);
            const docLink = document.createElement('div');
            docLink.innerHTML = docLinkHtml;
            element.appendChild(docLink);
        }
        </script>
    </div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-OutputArea-child">
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
    <div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain" tabindex="0">
    <pre>Shape of payments: (100000, 2)
    </pre>
    </div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell jp-MarkdownCell jp-Notebook-cell" id="cell-id=7014a2d5">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
    </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
    <h4 id="Join-the-tables-on-order_id-to-create-a-single-order-level-DataFrame">Join the tables on <code>order_id</code> to create a single order-level DataFrame<a class="anchor-link" href="#Join-the-tables-on-order_id-to-create-a-single-order-level-DataFrame">¶</a></h4><p>A unified "Order Analytical Record" (df_orders_full) is constructed by executing a series of inner joins on the order_id primary key. By systematically integrating df_orders, df_order_items, df_shipping, and df_payments, we ensure that our final dataset contains only synchronized records present across all functional domains. This approach allows us to establish a consistent and reliable foundation for all downstream analysis and modeling.</p>
    </div>
    </div>
    </div>
    </div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=5403e6e4">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea">
    <div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
    <div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
    <div class="cm-editor cm-s-jupyter">
    <div class="highlight hl-python"><pre><span></span><span class="c1"># Consolidate core order metadata with itemized transaction data</span>
    <span class="n">step1</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">merge</span><span class="p">(</span><span class="n">df_orders</span><span class="p">,</span> <span class="n">df_order_items</span><span class="p">,</span> <span class="n">on</span><span class="o">=</span><span class="s1">'order_id'</span><span class="p">,</span> <span class="n">how</span><span class="o">=</span><span class="s1">'inner'</span><span class="p">)</span>

    <span class="c1"># Enrich integrated records with logistics/shipping dimensions</span>
    <span class="n">step2</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">merge</span><span class="p">(</span><span class="n">step1</span><span class="p">,</span> <span class="n">df_shipping</span><span class="p">,</span> <span class="n">on</span><span class="o">=</span><span class="s1">'order_id'</span><span class="p">,</span> <span class="n">how</span><span class="o">=</span><span class="s1">'inner'</span><span class="p">)</span>

    <span class="c1"># Finalize the master analytical record with payment data</span>
    <span class="n">df_orders_full</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">merge</span><span class="p">(</span><span class="n">step2</span><span class="p">,</span> <span class="n">df_payments</span><span class="p">,</span> <span class="n">on</span><span class="o">=</span><span class="s1">'order_id'</span><span class="p">,</span> <span class="n">how</span><span class="o">=</span><span class="s1">'inner'</span><span class="p">)</span>

    <span class="c1"># Validation of the integrated master dataset</span>
    <span class="n">display</span><span class="p">(</span><span class="n">df_orders_full</span><span class="o">.</span><span class="n">head</span><span class="p">())</span>
    <span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s2">"Final result dataframe shape: </span><span class="si">{</span><span class="n">df_orders_full</span><span class="o">.</span><span class="n">shape</span><span class="si">}</span><span class="s2">"</span><span class="p">)</span>
    </pre></div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell-outputWrapper">
    <div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
    </div>
    <div class="jp-OutputArea jp-Cell-outputArea">
    <div class="jp-OutputArea-child">
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
    <div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output" data-mime-type="text/html" tabindex="0">
    <div class="colab-df-container" id="df-57f578d9-5d6b-49d9-abbf-d9aebd593ece">
    <div>
    <style scoped="">
        .dataframe tbody tr th:only-of-type {
            vertical-align: middle;
        }

        .dataframe tbody tr th {
            vertical-align: top;
        }

        .dataframe thead th {
            text-align: right;
        }
    </style>
    <table border="1" class="dataframe">
    <thead>
    <tr style="text-align: right;">
    <th></th>
    <th>order_id</th>
    <th>order_status</th>
    <th>order_purchase_hour</th>
    <th>order_purchase_dayofweek</th>
    <th>order_purchase_month</th>
    <th>order_total_value</th>
    <th>num_items</th>
    <th>num_unique_products</th>
    <th>num_unique_sellers</th>
    <th>total_item_price</th>
    <th>avg_item_price</th>
    <th>total_freight_value</th>
    <th>top_product_category</th>
    <th>customer_state</th>
    <th>payment_type</th>
    </tr>
    </thead>
    <tbody>
    <tr>
    <th>0</th>
    <td>sdv-id-whzjUX</td>
    <td>shipped</td>
    <td>10</td>
    <td>4</td>
    <td>4</td>
    <td>744.312535</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>352.420029</td>
    <td>369.966521</td>
    <td>68.790159</td>
    <td>construction_tools_construction</td>
    <td>Massachusetts</td>
    <td>voucher</td>
    </tr>
    <tr>
    <th>1</th>
    <td>sdv-id-gqShVM</td>
    <td>delivered</td>
    <td>19</td>
    <td>2</td>
    <td>4</td>
    <td>1030.521912</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>1580.187928</td>
    <td>1089.284136</td>
    <td>84.603289</td>
    <td>auto</td>
    <td>Ohio</td>
    <td>voucher</td>
    </tr>
    <tr>
    <th>2</th>
    <td>sdv-id-vtaqcY</td>
    <td>delivered</td>
    <td>18</td>
    <td>4</td>
    <td>8</td>
    <td>28.472994</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>45.969263</td>
    <td>36.969754</td>
    <td>24.022637</td>
    <td>furniture_decor</td>
    <td>Wisconsin</td>
    <td>voucher</td>
    </tr>
    <tr>
    <th>3</th>
    <td>sdv-id-xkqwdo</td>
    <td>invoiced</td>
    <td>23</td>
    <td>1</td>
    <td>8</td>
    <td>143.914263</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>146.023435</td>
    <td>126.755360</td>
    <td>16.945349</td>
    <td>consoles_games</td>
    <td>Michigan</td>
    <td>credit_card</td>
    </tr>
    <tr>
    <th>4</th>
    <td>sdv-id-sGyHvQ</td>
    <td>delivered</td>
    <td>19</td>
    <td>0</td>
    <td>2</td>
    <td>16.944537</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>30.525812</td>
    <td>22.797409</td>
    <td>17.785846</td>
    <td>air_conditioning</td>
    <td>Nevada</td>
    <td>credit_card</td>
    </tr>
    </tbody>
    </table>
    </div>
    <div class="colab-df-buttons">
    <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-57f578d9-5d6b-49d9-abbf-d9aebd593ece')" style="display:none;" title="Convert this dataframe to an interactive table.">
    <svg height="24px" viewbox="0 -960 960 960" xmlns="http://www.w3.org/2000/svg">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"></path>
    </svg>
    </button>
    <style>
        .colab-df-container {
        display:flex;
        gap: 12px;
        }

        .colab-df-convert {
        background-color: #E8F0FE;
        border: none;
        border-radius: 50%;
        cursor: pointer;
        display: none;
        fill: #1967D2;
        height: 32px;
        padding: 0 0 0 0;
        width: 32px;
        }

        .colab-df-convert:hover {
        background-color: #E2EBFA;
        box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
        fill: #174EA6;
        }

        .colab-df-buttons div {
        margin-bottom: 4px;
        }

        [theme=dark] .colab-df-convert {
        background-color: #3B4455;
        fill: #D2E3FC;
        }

        [theme=dark] .colab-df-convert:hover {
        background-color: #434B5C;
        box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
        filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
        fill: #FFFFFF;
        }
    </style>
    <script>
        const buttonEl =
            document.querySelector('#df-57f578d9-5d6b-49d9-abbf-d9aebd593ece button.colab-df-convert');
        buttonEl.style.display =
            google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
            const element = document.querySelector('#df-57f578d9-5d6b-49d9-abbf-d9aebd593ece');
            const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                        [key], {});
            if (!dataTable) return;

            const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
            element.innerHTML = '';
            dataTable['output_type'] = 'display_data';
            await google.colab.output.renderOutput(dataTable, element);
            const docLink = document.createElement('div');
            docLink.innerHTML = docLinkHtml;
            element.appendChild(docLink);
        }
        </script>
    </div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-OutputArea-child">
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
    <div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain" tabindex="0">
    <pre>Final result dataframe shape: (100000, 15)
    </pre>
    </div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell jp-MarkdownCell jp-Notebook-cell" id="cell-id=23132d79">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
    </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
    <hr/>
    <h3 id="1.2-Data-Cleaning">1.2 Data Cleaning<a class="anchor-link" href="#1.2-Data-Cleaning">¶</a></h3>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell jp-MarkdownCell jp-Notebook-cell" id="cell-id=7a4e5e9c">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
    </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
    <h4 id="Handle-missing-values">Handle missing values<a class="anchor-link" href="#Handle-missing-values">¶</a></h4><p>In this stage, we implement a robust data cleaning pipeline to ensure the integrity of our df_orders_full dataset. By applying statistical imputation, using medians for numerical features to mitigate outlier influence and modes for categorical attributes, the dataset is standardized for downstream modeling. This phase concludes with a structural filter to remove records with missing primary identifiers or critical payment metadata.</p>
    </div>
    </div>
    </div>
    </div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=a7e0967a">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea">
    <div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
    <div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
    <div class="cm-editor cm-s-jupyter">
    <div class="highlight hl-python"><pre><span></span><span class="c1"># Handle missing values</span>

    <span class="k">for</span> <span class="n">col</span> <span class="ow">in</span> <span class="n">df_orders_full</span><span class="o">.</span><span class="n">columns</span><span class="p">:</span>
    <span class="k">if</span> <span class="n">df_orders_full</span><span class="p">[</span><span class="n">col</span><span class="p">]</span><span class="o">.</span><span class="n">dtype</span> <span class="ow">in</span> <span class="p">[</span><span class="s1">'float64'</span><span class="p">,</span><span class="s1">'int64'</span><span class="p">]:</span>
        <span class="n">median_val</span> <span class="o">=</span> <span class="n">df_orders_full</span><span class="p">[</span><span class="n">col</span><span class="p">]</span><span class="o">.</span><span class="n">median</span><span class="p">()</span>
        <span class="n">df_orders_full</span><span class="p">[</span><span class="n">col</span><span class="p">]</span> <span class="o">=</span> <span class="n">df_orders_full</span><span class="p">[</span><span class="n">col</span><span class="p">]</span><span class="o">.</span><span class="n">fillna</span><span class="p">(</span><span class="n">median_val</span><span class="p">)</span>

    <span class="k">elif</span> <span class="n">df_orders_full</span><span class="p">[</span><span class="n">col</span><span class="p">]</span><span class="o">.</span><span class="n">dtype</span> <span class="o">==</span> <span class="s1">'object'</span><span class="p">:</span>
        <span class="n">mode_val</span> <span class="o">=</span> <span class="n">df_orders_full</span><span class="p">[</span><span class="n">col</span><span class="p">]</span><span class="o">.</span><span class="n">mode</span><span class="p">()[</span><span class="mi">0</span><span class="p">]</span>
        <span class="n">df_orders_full</span><span class="p">[</span><span class="n">col</span><span class="p">]</span> <span class="o">=</span> <span class="n">df_orders_full</span><span class="p">[</span><span class="n">col</span><span class="p">]</span><span class="o">.</span><span class="n">fillna</span><span class="p">(</span><span class="n">mode_val</span><span class="p">)</span>

    <span class="c1"># Enforce record-level integrity by removing rows with missing primary identifiers</span>
    <span class="n">df_orders_full</span><span class="o">.</span><span class="n">dropna</span><span class="p">(</span><span class="n">subset</span><span class="o">=</span><span class="p">[</span><span class="s1">'order_id'</span><span class="p">,</span><span class="s1">'payment_type'</span><span class="p">],</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>

    <span class="c1"># Validation of cleaned data state</span>
    <span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s2">"Dataframe df_orders_full shape: </span><span class="si">{</span><span class="n">df_orders_full</span><span class="o">.</span><span class="n">shape</span><span class="si">}</span><span class="s2">"</span><span class="p">)</span>
    </pre></div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell-outputWrapper">
    <div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
    </div>
    <div class="jp-OutputArea jp-Cell-outputArea">
    <div class="jp-OutputArea-child">
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
    <div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain" tabindex="0">
    <pre>Dataframe df_orders_full shape: (100000, 15)
    </pre>
    </div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell jp-MarkdownCell jp-Notebook-cell" id="cell-id=56711f4e">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
    </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
    <h4 id="Remove-clearly-invalid-numeric-records">Remove clearly invalid numeric records<a class="anchor-link" href="#Remove-clearly-invalid-numeric-records">¶</a></h4><p>The dataset is refined by removing records that violate fundamental business logic or physical constraints. A validation layer is applied to ensure that all transactional quantities and monetary values (specifically num_items, order_total_value, total_item_price, and total_freight_value) align with real-world operational standards. This step is critical for maintaining the integrity of downstream financial modeling and statistical distributions.</p>
    </div>
    </div>
    </div>
    </div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=6a5eb359">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea">
    <div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
    <div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
    <div class="cm-editor cm-s-jupyter">
    <div class="highlight hl-python"><pre><span></span><span class="c1"># Filter invalid numeric records</span>

    <span class="n">df_orders_full</span> <span class="o">=</span> <span class="n">df_orders_full</span><span class="p">[</span>
        <span class="p">(</span><span class="n">df_orders_full</span><span class="p">[</span><span class="s1">'num_items'</span><span class="p">]</span> <span class="o">&gt;</span> <span class="mi">0</span><span class="p">)</span> <span class="o">&amp;</span>
        <span class="p">(</span><span class="n">df_orders_full</span><span class="p">[</span><span class="s1">'order_total_value'</span><span class="p">]</span> <span class="o">&gt;</span> <span class="mi">0</span><span class="p">)</span> <span class="o">&amp;</span>
        <span class="p">(</span><span class="n">df_orders_full</span><span class="p">[</span><span class="s1">'total_item_price'</span><span class="p">]</span> <span class="o">&gt;=</span> <span class="mi">0</span><span class="p">)</span> <span class="o">&amp;</span>
        <span class="p">(</span><span class="n">df_orders_full</span><span class="p">[</span><span class="s1">'total_freight_value'</span><span class="p">]</span> <span class="o">&gt;=</span> <span class="mi">0</span><span class="p">)</span>
    <span class="p">]</span>

    <span class="c1"># Quantify the impact of the filtering process</span>
    <span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s2">"Dataframe df_orders_full shape: </span><span class="si">{</span><span class="n">df_orders_full</span><span class="o">.</span><span class="n">shape</span><span class="si">}</span><span class="s2">"</span><span class="p">)</span>
    </pre></div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell-outputWrapper">
    <div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
    </div>
    <div class="jp-OutputArea jp-Cell-outputArea">
    <div class="jp-OutputArea-child">
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
    <div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain" tabindex="0">
    <pre>Dataframe df_orders_full shape: (89175, 15)
    </pre>
    </div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell jp-MarkdownCell jp-Notebook-cell" id="cell-id=19e948c5">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
    </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
    <h4 id="Check-cleanliness-and-key-uniqueness">Check cleanliness and key uniqueness<a class="anchor-link" href="#Check-cleanliness-and-key-uniqueness">¶</a></h4><p>In this final verification stage, the dataset undergoes a rigorous quality audit to ensure it is "analysis-ready." This includes a global null-value assessment to confirm the success of previous imputation steps and a uniqueness check on the order_id primary key. These controls guarantee that the analytical grain remains strictly one record per order, preventing double-counting in downstream financial reporting.</p>
    </div>
    </div>
    </div>
    </div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=24810cfd">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea">
    <div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
    <div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
    <div class="cm-editor cm-s-jupyter">
    <div class="highlight hl-python"><pre><span></span><span class="c1"># Ensure zero missingness across all features</span>
    <span class="n">null_counts</span> <span class="o">=</span> <span class="n">df_orders_full</span><span class="o">.</span><span class="n">isnull</span><span class="p">()</span><span class="o">.</span><span class="n">sum</span><span class="p">()</span><span class="o">.</span><span class="n">sum</span><span class="p">()</span>

    <span class="k">if</span> <span class="n">null_counts</span> <span class="o">==</span> <span class="mi">0</span><span class="p">:</span>
    <span class="nb">print</span><span class="p">(</span><span class="s2">"There are no null values in dataset"</span><span class="p">)</span>
    <span class="k">else</span><span class="p">:</span>
    <span class="nb">print</span><span class="p">(</span><span class="s2">"There are some null values existing in dataset"</span><span class="p">)</span>
    <span class="nb">print</span><span class="p">(</span><span class="n">null_counts</span><span class="p">[</span><span class="n">null_counts</span><span class="o">&gt;</span><span class="mi">0</span><span class="p">])</span>

    <span class="c1"># Validate the primary key at the order grain</span>
    <span class="n">total_rows</span> <span class="o">=</span> <span class="n">df_orders_full</span><span class="o">.</span><span class="n">shape</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span>
    <span class="n">unique_orders</span> <span class="o">=</span> <span class="n">df_orders_full</span><span class="p">[</span><span class="s1">'order_id'</span><span class="p">]</span><span class="o">.</span><span class="n">nunique</span><span class="p">()</span>

    <span class="k">if</span> <span class="n">total_rows</span> <span class="o">==</span> <span class="n">unique_orders</span><span class="p">:</span>
    <span class="nb">print</span><span class="p">(</span><span class="s2">"Rows are unique"</span><span class="p">)</span>
    <span class="k">else</span><span class="p">:</span>
    <span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s2">"There are </span><span class="si">{</span><span class="n">total_rows</span><span class="w"> </span><span class="o">-</span><span class="w"> </span><span class="n">unique_orders</span><span class="si">}</span><span class="s2"> duplicated rows"</span><span class="p">)</span>
    </pre></div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell-outputWrapper">
    <div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
    </div>
    <div class="jp-OutputArea jp-Cell-outputArea">
    <div class="jp-OutputArea-child">
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
    <div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain" tabindex="0">
    <pre>There are no null values in dataset
    Rows are unique
    </pre>
    </div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell jp-MarkdownCell jp-Notebook-cell" id="cell-id=bc3964f2">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
    </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
    <hr/>
    <h3 id="1.3-Data-Transformation">1.3 Data Transformation<a class="anchor-link" href="#1.3-Data-Transformation">¶</a></h3><p>Advanced sanity checks are applied to the df_orders_full dataset to ensure internal consistency between interrelated metrics. By enforcing strict logical constraints the data integrity is solidified for downstream feature engineering.</p>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell jp-MarkdownCell jp-Notebook-cell" id="cell-id=776b7675">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
    </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
    <h4 id="Sanity-checks-on-counts-and-values">Sanity checks on counts and values<a class="anchor-link" href="#Sanity-checks-on-counts-and-values">¶</a></h4><ol>
    <li>The total item count must logically be greater than or equal to the count of unique products</li>
    <li>The total order value must encompass the combined sum of item prices and freight charges</li>
    </ol>
    </div>
    </div>
    </div>
    </div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=4ed4ca06">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea">
    <div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
    <div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
    <div class="cm-editor cm-s-jupyter">
    <div class="highlight hl-python"><pre><span></span><span class="c1"># Apply logical consistency constraints to ensure transactional integrity</span>

    <span class="n">df_orders_full</span> <span class="o">=</span> <span class="n">df_orders_full</span><span class="p">[</span>
        <span class="p">(</span><span class="n">df_orders_full</span><span class="p">[</span><span class="s1">'num_items'</span><span class="p">]</span> <span class="o">&gt;=</span> <span class="n">df_orders_full</span><span class="p">[</span><span class="s1">'num_unique_products'</span><span class="p">])</span> <span class="o">&amp;</span>
        <span class="p">(</span><span class="n">df_orders_full</span><span class="p">[</span><span class="s1">'order_total_value'</span><span class="p">]</span> <span class="o">&gt;=</span> <span class="n">df_orders_full</span><span class="p">[</span><span class="s1">'total_item_price'</span><span class="p">]</span> <span class="o">+</span> <span class="n">df_orders_full</span><span class="p">[</span><span class="s1">'total_freight_value'</span><span class="p">])</span>
    <span class="p">]</span>

    <span class="c1"># Audit the dataset following the application of logical constraints</span>
    <span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s2">"Dataframe df_orders_full shape: </span><span class="si">{</span><span class="n">df_orders_full</span><span class="o">.</span><span class="n">shape</span><span class="si">}</span><span class="s2">"</span><span class="p">)</span>
    </pre></div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell-outputWrapper">
    <div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
    </div>
    <div class="jp-OutputArea jp-Cell-outputArea">
    <div class="jp-OutputArea-child">
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
    <div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain" tabindex="0">
    <pre>Dataframe df_orders_full shape: (46287, 15)
    </pre>
    </div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell jp-MarkdownCell jp-Notebook-cell" id="cell-id=bf21082c">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
    </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
    <h4 id="Create-order_value_per_item">Create <code>order_value_per_item</code><a class="anchor-link" href="#Create-order_value_per_item">¶</a></h4><p>By calculating the order_value_per_item, a normalized unit-value feature is established. This metric is essential for identifying high-margin transactions and segmenting consumer purchasing behavior based on average item cost rather than gross transaction totals.</p>
    </div>
    </div>
    </div>
    </div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=7e20077f">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea">
    <div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
    <div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
    <div class="cm-editor cm-s-jupyter">
    <div class="highlight hl-python"><pre><span></span><span class="c1"># order_value_per_item: Captures the average economic value of each unit within a basket</span>

    <span class="n">df_orders_full</span><span class="p">[</span><span class="s1">'order_value_per_item'</span><span class="p">]</span> <span class="o">=</span> <span class="n">df_orders_full</span><span class="p">[</span><span class="s1">'total_item_price'</span><span class="p">]</span> <span class="o">/</span> <span class="n">df_orders_full</span><span class="p">[</span><span class="s1">'num_items'</span><span class="p">]</span>

    <span class="c1"># Validate the addition of the new feature dimension</span>
    <span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s2">"Dataframe df_orders_full shape: </span><span class="si">{</span><span class="n">df_orders_full</span><span class="o">.</span><span class="n">shape</span><span class="si">}</span><span class="s2">"</span><span class="p">)</span>
    </pre></div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell-outputWrapper">
    <div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
    </div>
    <div class="jp-OutputArea jp-Cell-outputArea">
    <div class="jp-OutputArea-child">
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
    <div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain" tabindex="0">
    <pre>Dataframe df_orders_full shape: (46287, 16)
    </pre>
    </div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell jp-MarkdownCell jp-Notebook-cell" id="cell-id=c4a0ba77">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
    </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
    <h4 id="Create-order_size_category">Create <code>order_size_category</code><a class="anchor-link" href="#Create-order_size_category">¶</a></h4><p>Segmentation logic is applied to categorize transactions based on their physical volume. By defining the order_size_category attribute, the continuous num_items variable is transformed into discrete classes (Small, Medium, and Large). This categorization facilitates high-level comparative analysis, allowing for the identification of distinct purchasing patterns and logistics requirements across different order scales.</p>
    </div>
    </div>
    </div>
    </div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs" id="cell-id=bcf78d36">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea">
    <div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
    <div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
    <div class="cm-editor cm-s-jupyter">
    <div class="highlight hl-python"><pre><span></span><span class="c1"># Small: 1-2 items | Medium: 3-5 items | Large: &gt;5 items</span>

    <span class="n">conditions</span> <span class="o">=</span> <span class="p">[</span>
        <span class="p">(</span><span class="n">df_orders_full</span><span class="p">[</span><span class="s1">'num_items'</span><span class="p">]</span> <span class="o">&lt;=</span> <span class="mi">2</span><span class="p">),</span>
        <span class="p">(</span><span class="n">df_orders_full</span><span class="p">[</span><span class="s1">'num_items'</span><span class="p">]</span> <span class="o">&lt;=</span> <span class="mi">5</span><span class="p">),</span>
        <span class="p">(</span><span class="n">df_orders_full</span><span class="p">[</span><span class="s1">'num_items'</span><span class="p">]</span> <span class="o">&gt;</span> <span class="mi">2</span><span class="p">)</span>
    <span class="p">]</span>

    <span class="n">choices</span> <span class="o">=</span> <span class="p">[</span><span class="s1">'Small'</span><span class="p">,</span><span class="s1">'Medium'</span><span class="p">,</span><span class="s1">'Large'</span><span class="p">]</span>

    <span class="n">df_orders_full</span><span class="p">[</span><span class="s1">'order_size_category'</span><span class="p">]</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">select</span><span class="p">(</span><span class="n">conditions</span><span class="p">,</span> <span class="n">choices</span><span class="p">,</span> <span class="n">default</span><span class="o">=</span><span class="s1">'unknown'</span><span class="p">)</span>
    </pre></div>
    </div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell jp-MarkdownCell jp-Notebook-cell" id="cell-id=abfa04c8">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
    </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
    <h4 id="Final-transformation-check">Final transformation check<a class="anchor-link" href="#Final-transformation-check">¶</a></h4><p>A comprehensive state-of-health check is performed on the fully transformed df_orders_full dataset. By verifying the absence of null values across all engineered features and auditing the final schema via info(), we certify the data as 'production-ready.' This rigorous validation ensures that our downstream exploratory analytics and modeling are built upon a high-integrity foundation, where all data types and record counts are strictly confirmed.</p>
    </div>
    </div>
    </div>
    </div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=742a2e1e">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea">
    <div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
    <div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
    <div class="cm-editor cm-s-jupyter">
    <div class="highlight hl-python"><pre><span></span><span class="c1"># Ensure feature engineering did not introduce missingness</span>
    <span class="nb">print</span><span class="p">(</span><span class="n">df_orders_full</span><span class="o">.</span><span class="n">isnull</span><span class="p">()</span><span class="o">.</span><span class="n">sum</span><span class="p">())</span>

    <span class="c1"># Inspect data types and memory usage</span>
    <span class="n">df_orders_full</span><span class="o">.</span><span class="n">info</span><span class="p">()</span>

    <span class="c1"># Capture the terminal shape of the workflow</span>
    <span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s2">"Final Shape of Dataframe df_orders_full </span><span class="si">{</span><span class="n">df_orders_full</span><span class="o">.</span><span class="n">shape</span><span class="si">}</span><span class="s2">"</span><span class="p">)</span>

    <span class="c1"># Review the enriched record structure</span>
    <span class="n">display</span><span class="p">(</span><span class="n">df_orders_full</span><span class="o">.</span><span class="n">head</span><span class="p">())</span>
    </pre></div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell-outputWrapper">
    <div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
    </div>
    <div class="jp-OutputArea jp-Cell-outputArea">
    <div class="jp-OutputArea-child">
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
    <div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain" tabindex="0">
    <pre>order_id                    0
    order_status                0
    order_purchase_hour         0
    order_purchase_dayofweek    0
    order_purchase_month        0
    order_total_value           0
    num_items                   0
    num_unique_products         0
    num_unique_sellers          0
    total_item_price            0
    avg_item_price              0
    total_freight_value         0
    top_product_category        0
    customer_state              0
    payment_type                0
    order_value_per_item        0
    order_size_category         0
    dtype: int64
    &lt;class 'pandas.core.frame.DataFrame'&gt;
    Index: 46287 entries, 0 to 99997
    Data columns (total 17 columns):
    #   Column                    Non-Null Count  Dtype  
    ---  ------                    --------------  -----  
    0   order_id                  46287 non-null  object 
    1   order_status              46287 non-null  object 
    2   order_purchase_hour       46287 non-null  int64  
    3   order_purchase_dayofweek  46287 non-null  int64  
    4   order_purchase_month      46287 non-null  int64  
    5   order_total_value         46287 non-null  float64
    6   num_items                 46287 non-null  int64  
    7   num_unique_products       46287 non-null  int64  
    8   num_unique_sellers        46287 non-null  int64  
    9   total_item_price          46287 non-null  float64
    10  avg_item_price            46287 non-null  float64
    11  total_freight_value       46287 non-null  float64
    12  top_product_category      46287 non-null  object 
    13  customer_state            46287 non-null  object 
    14  payment_type              46287 non-null  object 
    15  order_value_per_item      46287 non-null  float64
    16  order_size_category       46287 non-null  object 
    dtypes: float64(5), int64(6), object(6)
    memory usage: 6.4+ MB
    Final Shape of Dataframe df_orders_full (46287, 17)
    </pre>
    </div>
    </div>
    <div class="jp-OutputArea-child">
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
    <div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output" data-mime-type="text/html" tabindex="0">
    <div class="colab-df-container" id="df-26d9b218-9730-42a9-b413-e7bd8acec3d2">
    <div>
    <style scoped="">
        .dataframe tbody tr th:only-of-type {
            vertical-align: middle;
        }

        .dataframe tbody tr th {
            vertical-align: top;
        }

        .dataframe thead th {
            text-align: right;
        }
    </style>
    <table border="1" class="dataframe">
    <thead>
    <tr style="text-align: right;">
    <th></th>
    <th>order_id</th>
    <th>order_status</th>
    <th>order_purchase_hour</th>
    <th>order_purchase_dayofweek</th>
    <th>order_purchase_month</th>
    <th>order_total_value</th>
    <th>num_items</th>
    <th>num_unique_products</th>
    <th>num_unique_sellers</th>
    <th>total_item_price</th>
    <th>avg_item_price</th>
    <th>total_freight_value</th>
    <th>top_product_category</th>
    <th>customer_state</th>
    <th>payment_type</th>
    <th>order_value_per_item</th>
    <th>order_size_category</th>
    </tr>
    </thead>
    <tbody>
    <tr>
    <th>0</th>
    <td>sdv-id-whzjUX</td>
    <td>shipped</td>
    <td>10</td>
    <td>4</td>
    <td>4</td>
    <td>744.312535</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>352.420029</td>
    <td>369.966521</td>
    <td>68.790159</td>
    <td>construction_tools_construction</td>
    <td>Massachusetts</td>
    <td>voucher</td>
    <td>352.420029</td>
    <td>Small</td>
    </tr>
    <tr>
    <th>5</th>
    <td>sdv-id-dbopoJ</td>
    <td>delivered</td>
    <td>19</td>
    <td>2</td>
    <td>3</td>
    <td>1556.667902</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>289.242639</td>
    <td>1354.621410</td>
    <td>15.394619</td>
    <td>health_beauty</td>
    <td>Vermont</td>
    <td>credit_card</td>
    <td>289.242639</td>
    <td>Small</td>
    </tr>
    <tr>
    <th>8</th>
    <td>sdv-id-FSEOvM</td>
    <td>delivered</td>
    <td>15</td>
    <td>4</td>
    <td>8</td>
    <td>62.060506</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>26.893468</td>
    <td>48.485654</td>
    <td>18.751282</td>
    <td>luggage_accessories</td>
    <td>South Carolina</td>
    <td>debit_card</td>
    <td>26.893468</td>
    <td>Small</td>
    </tr>
    <tr>
    <th>12</th>
    <td>sdv-id-bQcBUR</td>
    <td>delivered</td>
    <td>21</td>
    <td>0</td>
    <td>8</td>
    <td>73.873470</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>37.790896</td>
    <td>75.704909</td>
    <td>8.670875</td>
    <td>computers_accessories</td>
    <td>Kentucky</td>
    <td>credit_card</td>
    <td>37.790896</td>
    <td>Small</td>
    </tr>
    <tr>
    <th>14</th>
    <td>sdv-id-MPxIXB</td>
    <td>delivered</td>
    <td>13</td>
    <td>5</td>
    <td>5</td>
    <td>361.961537</td>
    <td>3</td>
    <td>3</td>
    <td>3</td>
    <td>169.528323</td>
    <td>50.132979</td>
    <td>34.731146</td>
    <td>pet_shop</td>
    <td>Missouri</td>
    <td>voucher</td>
    <td>56.509441</td>
    <td>Medium</td>
    </tr>
    </tbody>
    </table>
    </div>
    <div class="colab-df-buttons">
    <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-26d9b218-9730-42a9-b413-e7bd8acec3d2')" style="display:none;" title="Convert this dataframe to an interactive table.">
    <svg height="24px" viewbox="0 -960 960 960" xmlns="http://www.w3.org/2000/svg">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"></path>
    </svg>
    </button>
    <style>
        .colab-df-container {
        display:flex;
        gap: 12px;
        }

        .colab-df-convert {
        background-color: #E8F0FE;
        border: none;
        border-radius: 50%;
        cursor: pointer;
        display: none;
        fill: #1967D2;
        height: 32px;
        padding: 0 0 0 0;
        width: 32px;
        }

        .colab-df-convert:hover {
        background-color: #E2EBFA;
        box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
        fill: #174EA6;
        }

        .colab-df-buttons div {
        margin-bottom: 4px;
        }

        [theme=dark] .colab-df-convert {
        background-color: #3B4455;
        fill: #D2E3FC;
        }

        [theme=dark] .colab-df-convert:hover {
        background-color: #434B5C;
        box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
        filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
        fill: #FFFFFF;
        }
    </style>
    <script>
        const buttonEl =
            document.querySelector('#df-26d9b218-9730-42a9-b413-e7bd8acec3d2 button.colab-df-convert');
        buttonEl.style.display =
            google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
            const element = document.querySelector('#df-26d9b218-9730-42a9-b413-e7bd8acec3d2');
            const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                        [key], {});
            if (!dataTable) return;

            const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
            element.innerHTML = '';
            dataTable['output_type'] = 'display_data';
            await google.colab.output.renderOutput(dataTable, element);
            const docLink = document.createElement('div');
            docLink.innerHTML = docLinkHtml;
            element.appendChild(docLink);
        }
        </script>
    </div>
    </div>
    </div>
    </div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell jp-MarkdownCell jp-Notebook-cell" id="cell-id=96f2182d">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
    </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
    <h3 id="1.4-Data-Storage">1.4 Data Storage<a class="anchor-link" href="#1.4-Data-Storage">¶</a></h3><p>The refined and validated dataset is persisted to disk. By exporting df_orders_full as a standardized flat file (ecommerce_orders_cleaned.csv), a "Single Source of Truth" is established.</p>
    <h4 id="1.4A-Save-cleaned-dataset">1.4A Save cleaned dataset<a class="anchor-link" href="#1.4A-Save-cleaned-dataset">¶</a></h4>
    </div>
    </div>
    </div>
    </div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs" id="cell-id=9ac046b6">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea">
    <div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
    <div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
    <div class="cm-editor cm-s-jupyter">
    <div class="highlight hl-python"><pre><span></span><span class="c1"># Persist the high-integrity analytical dataset for downstream consumption</span>

    <span class="n">df_orders_full</span><span class="o">.</span><span class="n">to_csv</span><span class="p">(</span><span class="s1">'ecommerce_orders_cleaned.csv'</span><span class="p">,</span> <span class="n">index</span><span class="o">=</span><span class="kc">False</span><span class="p">)</span>
    </pre></div>
    </div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell jp-MarkdownCell jp-Notebook-cell" id="cell-id=9e9af0e9">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
    </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
    <hr/>
    <h2 id="Part-2:-EDA-&amp;-Data-Visualization">Part 2: EDA &amp; Data Visualization<a class="anchor-link" href="#Part-2:-EDA-&amp;-Data-Visualization">¶</a></h2><p>We now reload the cleaned dataset and explore it. By reloading the validated ecommerce_orders_cleaned.csv into a fresh workspace, a stateless environment is established for visualization and statistical modeling. This ensures that all subsequent insights are derived from the finalized "Single Source of Truth," maintaining consistency across the reporting lifecycle.</p>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell jp-MarkdownCell jp-Notebook-cell" id="cell-id=1a913f7c">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
    </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
    <h3 id="2.0-Load-Transformed-Dataset">2.0 Load Transformed Dataset<a class="anchor-link" href="#2.0-Load-Transformed-Dataset">¶</a></h3><h4 id="2.0-Reload-CSV">2.0 Reload CSV<a class="anchor-link" href="#2.0-Reload-CSV">¶</a></h4>
    </div>
    </div>
    </div>
    </div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=c1b5ae27">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea">
    <div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
    <div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
    <div class="cm-editor cm-s-jupyter">
    <div class="highlight hl-python"><pre><span></span><span class="c1"># Load the analytical record</span>

    <span class="n">df_orders_cleaned</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s1">'ecommerce_orders_cleaned.csv'</span><span class="p">)</span>

    <span class="c1"># Verify data availability and dimensional integrity for the EDA session</span>
    <span class="n">display</span><span class="p">(</span><span class="n">df_orders_cleaned</span><span class="o">.</span><span class="n">head</span><span class="p">())</span>
    <span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s2">"Cleaned Dataframe Shape: </span><span class="si">{</span><span class="n">df_orders_cleaned</span><span class="o">.</span><span class="n">shape</span><span class="si">}</span><span class="s2">"</span><span class="p">)</span>
    </pre></div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell-outputWrapper">
    <div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
    </div>
    <div class="jp-OutputArea jp-Cell-outputArea">
    <div class="jp-OutputArea-child">
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
    <div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output" data-mime-type="text/html" tabindex="0">
    <div class="colab-df-container" id="df-56804ecb-a474-4b90-987e-53b652672cf4">
    <div>
    <style scoped="">
        .dataframe tbody tr th:only-of-type {
            vertical-align: middle;
        }

        .dataframe tbody tr th {
            vertical-align: top;
        }

        .dataframe thead th {
            text-align: right;
        }
    </style>
    <table border="1" class="dataframe">
    <thead>
    <tr style="text-align: right;">
    <th></th>
    <th>order_id</th>
    <th>order_status</th>
    <th>order_purchase_hour</th>
    <th>order_purchase_dayofweek</th>
    <th>order_purchase_month</th>
    <th>order_total_value</th>
    <th>num_items</th>
    <th>num_unique_products</th>
    <th>num_unique_sellers</th>
    <th>total_item_price</th>
    <th>avg_item_price</th>
    <th>total_freight_value</th>
    <th>top_product_category</th>
    <th>customer_state</th>
    <th>payment_type</th>
    <th>order_value_per_item</th>
    <th>order_size_category</th>
    </tr>
    </thead>
    <tbody>
    <tr>
    <th>0</th>
    <td>sdv-id-whzjUX</td>
    <td>shipped</td>
    <td>10</td>
    <td>4</td>
    <td>4</td>
    <td>744.312535</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>352.420029</td>
    <td>369.966521</td>
    <td>68.790159</td>
    <td>construction_tools_construction</td>
    <td>Massachusetts</td>
    <td>voucher</td>
    <td>352.420029</td>
    <td>Small</td>
    </tr>
    <tr>
    <th>1</th>
    <td>sdv-id-dbopoJ</td>
    <td>delivered</td>
    <td>19</td>
    <td>2</td>
    <td>3</td>
    <td>1556.667902</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>289.242639</td>
    <td>1354.621410</td>
    <td>15.394619</td>
    <td>health_beauty</td>
    <td>Vermont</td>
    <td>credit_card</td>
    <td>289.242639</td>
    <td>Small</td>
    </tr>
    <tr>
    <th>2</th>
    <td>sdv-id-FSEOvM</td>
    <td>delivered</td>
    <td>15</td>
    <td>4</td>
    <td>8</td>
    <td>62.060506</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>26.893468</td>
    <td>48.485654</td>
    <td>18.751282</td>
    <td>luggage_accessories</td>
    <td>South Carolina</td>
    <td>debit_card</td>
    <td>26.893468</td>
    <td>Small</td>
    </tr>
    <tr>
    <th>3</th>
    <td>sdv-id-bQcBUR</td>
    <td>delivered</td>
    <td>21</td>
    <td>0</td>
    <td>8</td>
    <td>73.873470</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>37.790896</td>
    <td>75.704909</td>
    <td>8.670875</td>
    <td>computers_accessories</td>
    <td>Kentucky</td>
    <td>credit_card</td>
    <td>37.790896</td>
    <td>Small</td>
    </tr>
    <tr>
    <th>4</th>
    <td>sdv-id-MPxIXB</td>
    <td>delivered</td>
    <td>13</td>
    <td>5</td>
    <td>5</td>
    <td>361.961537</td>
    <td>3</td>
    <td>3</td>
    <td>3</td>
    <td>169.528323</td>
    <td>50.132979</td>
    <td>34.731146</td>
    <td>pet_shop</td>
    <td>Missouri</td>
    <td>voucher</td>
    <td>56.509441</td>
    <td>Medium</td>
    </tr>
    </tbody>
    </table>
    </div>
    <div class="colab-df-buttons">
    <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-56804ecb-a474-4b90-987e-53b652672cf4')" style="display:none;" title="Convert this dataframe to an interactive table.">
    <svg height="24px" viewbox="0 -960 960 960" xmlns="http://www.w3.org/2000/svg">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"></path>
    </svg>
    </button>
    <style>
        .colab-df-container {
        display:flex;
        gap: 12px;
        }

        .colab-df-convert {
        background-color: #E8F0FE;
        border: none;
        border-radius: 50%;
        cursor: pointer;
        display: none;
        fill: #1967D2;
        height: 32px;
        padding: 0 0 0 0;
        width: 32px;
        }

        .colab-df-convert:hover {
        background-color: #E2EBFA;
        box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
        fill: #174EA6;
        }

        .colab-df-buttons div {
        margin-bottom: 4px;
        }

        [theme=dark] .colab-df-convert {
        background-color: #3B4455;
        fill: #D2E3FC;
        }

        [theme=dark] .colab-df-convert:hover {
        background-color: #434B5C;
        box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
        filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
        fill: #FFFFFF;
        }
    </style>
    <script>
        const buttonEl =
            document.querySelector('#df-56804ecb-a474-4b90-987e-53b652672cf4 button.colab-df-convert');
        buttonEl.style.display =
            google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
            const element = document.querySelector('#df-56804ecb-a474-4b90-987e-53b652672cf4');
            const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                        [key], {});
            if (!dataTable) return;

            const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
            element.innerHTML = '';
            dataTable['output_type'] = 'display_data';
            await google.colab.output.renderOutput(dataTable, element);
            const docLink = document.createElement('div');
            docLink.innerHTML = docLinkHtml;
            element.appendChild(docLink);
        }
        </script>
    </div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-OutputArea-child">
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
    <div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain" tabindex="0">
    <pre>Cleaned Dataframe Shape: (46287, 17)
    </pre>
    </div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell jp-MarkdownCell jp-Notebook-cell" id="cell-id=73e792db">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
    </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
    <h3 id="2.1-Unique-Categories-and-Payment-Types">2.1 Unique Categories and Payment Types<a class="anchor-link" href="#2.1-Unique-Categories-and-Payment-Types">¶</a></h3><p>A high-level census of the marketplace dimensions is conducted to quantify product diversity and financial channel preferences. By identifying the cardinality of product categories and payment methods, the operational breadth of the platform is established. The subsequent ranking of high-volume categories and dominant payment types provides critical insights into consumer demand and transaction behavior, essential for targeted marketing and payment infrastructure optimization.</p>
    </div>
    </div>
    </div>
    </div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=dc776346">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea">
    <div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
    <div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
    <div class="cm-editor cm-s-jupyter">
    <div class="highlight hl-python"><pre><span></span><span class="c1"># Quantify categorical cardinality and primary transactional drivers</span>
    <span class="n">unique_categories</span> <span class="o">=</span> <span class="n">df_orders_cleaned</span><span class="p">[</span><span class="s1">'top_product_category'</span><span class="p">]</span><span class="o">.</span><span class="n">nunique</span><span class="p">()</span>
    <span class="n">unique_payments</span> <span class="o">=</span> <span class="n">df_orders_cleaned</span><span class="p">[</span><span class="s1">'payment_type'</span><span class="p">]</span><span class="o">.</span><span class="n">nunique</span><span class="p">()</span>

    <span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s2">"Number of unique product categories: </span><span class="si">{</span><span class="n">unique_categories</span><span class="si">}</span><span class="s2">"</span><span class="p">)</span>
    <span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s2">"Number of unique payment types: </span><span class="si">{</span><span class="n">unique_payments</span><span class="si">}</span><span class="s2">"</span><span class="p">)</span>

    <span class="c1"># Identify the top 5 high-velocity product categories</span>
    <span class="n">top_categories</span> <span class="o">=</span> <span class="n">df_orders_cleaned</span><span class="p">[</span><span class="s1">'top_product_category'</span><span class="p">]</span><span class="o">.</span><span class="n">value_counts</span><span class="p">()</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">5</span><span class="p">)</span>
    <span class="nb">print</span><span class="p">(</span><span class="s2">"--- Top 5 Product Categories ---"</span><span class="p">)</span>
    <span class="nb">print</span><span class="p">(</span><span class="n">top_categories</span><span class="p">)</span>

    <span class="c1"># Identify the top 3 dominant payment channels</span>
    <span class="n">top_payments</span> <span class="o">=</span> <span class="n">df_orders_cleaned</span><span class="p">[</span><span class="s1">'payment_type'</span><span class="p">]</span><span class="o">.</span><span class="n">value_counts</span><span class="p">()</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="mi">3</span><span class="p">)</span>
    <span class="nb">print</span><span class="p">(</span><span class="s2">"--- Top 5 Payment Types ---"</span><span class="p">)</span>
    <span class="nb">print</span><span class="p">(</span><span class="n">top_payments</span><span class="p">)</span>
    </pre></div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell-outputWrapper">
    <div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
    </div>
    <div class="jp-OutputArea jp-Cell-outputArea">
    <div class="jp-OutputArea-child">
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
    <div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain" tabindex="0">
    <pre>Number of unique product categories: 71
    Number of unique payment types: 5
    --- Top 5 Product Categories ---
    top_product_category
    bed_bath_table           6419
    health_beauty            4208
    furniture_decor          3413
    computers_accessories    3386
    telephony                2570
    Name: count, dtype: int64
    --- Top 5 Payment Types ---
    payment_type
    credit_card    27987
    voucher        13812
    points          2532
    Name: count, dtype: int64
    </pre>
    </div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell jp-MarkdownCell jp-Notebook-cell" id="cell-id=57767fad">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
    </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
    <h3 id="2.2-Bar-Chart-of-Orders-by-Product-Category">2.2 Bar Chart of Orders by Product Category<a class="anchor-link" href="#2.2-Bar-Chart-of-Orders-by-Product-Category">¶</a></h3><p>The transactional volume is visualized across the diverse product landscape to identify primary market drivers. By executing a ranked frequency analysis of the top_product_category attribute, we establish a comprehensive demand profile for the platform. This visualization is essential for inventory prioritization, as it allows us to understand which vertical segments contribute most significantly to our overall order throughput.</p>
    </div>
    </div>
    </div>
    </div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=6e622d28">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea">
    <div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
    <div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
    <div class="cm-editor cm-s-jupyter">
    <div class="highlight hl-python"><pre><span></span><span class="c1"># Configure visual parameters for executive reporting</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">12</span><span class="p">,</span><span class="mi">15</span><span class="p">))</span>

    <span class="c1"># Determine categorical ranking by descending transaction frequency</span>
    <span class="n">category_order</span> <span class="o">=</span> <span class="n">df_orders_cleaned</span><span class="p">[</span><span class="s1">'top_product_category'</span><span class="p">]</span><span class="o">.</span><span class="n">value_counts</span><span class="p">()</span><span class="o">.</span><span class="n">index</span>

    <span class="c1"># Render categorical velocity distribution</span>
    <span class="n">sns</span><span class="o">.</span><span class="n">countplot</span><span class="p">(</span>
        <span class="n">data</span> <span class="o">=</span> <span class="n">df_orders_cleaned</span><span class="p">,</span>
        <span class="n">y</span> <span class="o">=</span> <span class="s1">'top_product_category'</span><span class="p">,</span>
        <span class="n">order</span> <span class="o">=</span> <span class="n">category_order</span><span class="p">,</span>
        <span class="n">color</span><span class="o">=</span><span class="s1">'steelblue'</span><span class="p">,</span>
    <span class="p">)</span>

    <span class="c1"># Refine chart aesthetics for professional presentation</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">'Total Orders by Product Category'</span><span class="p">,</span> <span class="n">fontsize</span> <span class="o">=</span> <span class="mi">16</span><span class="p">,</span> <span class="n">pad</span> <span class="o">=</span> <span class="mi">25</span><span class="p">)</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">'Number of Orders'</span><span class="p">,</span> <span class="n">fontsize</span> <span class="o">=</span> <span class="mi">12</span><span class="p">)</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">'Product Category'</span><span class="p">,</span> <span class="n">fontsize</span> <span class="o">=</span> <span class="mi">8</span><span class="p">)</span>

    <span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
    </pre></div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell-outputWrapper">
    <div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
    </div>
    <div class="jp-OutputArea jp-Cell-outputArea">
    <div class="jp-OutputArea-child">
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
    <div class="jp-RenderedImage jp-OutputArea-output" tabindex="0">
    <img alt="No description has been provided for this image" class="" src="data:image/png;base64,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hIaGsmXLFnbt2sX06dN566230tWbOXMmYWFhvPfee8b+N2/ezEcffUSxYsXw9vamZMmS3L59m507dzJixAhCQkL4+OOPM/W8EhMT6dmzJzY2Nrz99tvEx8ezceNG5s2bx19//cWMGTMoU6YM9erVY9++ffz666+0atUqXTtbtmwBoE2bNpnq92leffVV9uzZQ3h4eLp7K1eu5PDhw7zzzjtUqFDBeD2z8zPVuHHjWLNmDaVLl6Znz57ky5ePY8eO0b17dwoUKJAj49i0aRPDhg2jaNGitGnThgIFCnDo0CFmzJjBb7/9xtKlSylcuDDDhg1jxYoVhIaG0qlTJ+zs7KhRo8YT216+fDmJiYl07tyZ11577Yllu3fvTrdu3TA3Nzdeu3//Pp07d+bPP/+kbt26+Pj4kJiYSGBgIMuXL2ffvn388ssvFChQ4Km/01FRUXTq1Im//voLFxcXWrRowb179wgICGD8+PEcOHCAWbNmYWJiAsCNGzfo3LkzkZGR1K1bl3r16hEeHs4nn3zC+++/n+EYVq9ezejRo8mfPz9vvfUWtra2REREsH37dt5//31GjBjBu+++m67eP3+HqlWrxv79+/n555/x8fFJVz51Lrdq1QozM/1nqIj8yxhERERE5Lk6ePCgoWrVqoY2bdqku7djxw5D1apVDW+99Zbhzp07ae5t2LDBULVqVUOLFi3SXG/SpImhatWqhtDQ0DTXhw0bZqhataph1qxZaa5fu3bNULNmTUPVqlUNf/zxh/H6zz//bKhataph+PDhTx3DlClTDFWrVjV88803Ty2bqmnTpoaqVasaTp06ZbxWtWpVw5tvvmno06dPuvIffvhhhn1cuXLFULt2bUPVqlUN3bp1M16Pjo421K5d21CrVi3D+fPn09Q5ffq04c033zTUrVvXcPfuXeP11GfXtm1bQ0JCQpo6b7/9drpnZDAYDHfv3jU0a9bM4ObmZnjw4METx5z6XVetWtUwevToNPdu3bplcHFxMVStWtUQFBRkMBgMho0bNxqqVq1q6NmzZ7q2zp49+9h587h+n1b2008/NVStWtWwcOFC47Vu3boZqlatamjSpIkhJiYmTfmszs8LFy4Yqlataqhbt64hMjIyTfkvvvjC+GwOHjyYrv9Hr6VKnaMffvih8dqNGzcMtWrVMtStW9cQERGRpvygQYMMVatW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4/Dx8cHa2prt27cb53iqixcvsm3bNqytrfH29s74YT1Gu3btAJg2bRoRERH4+PjkeqJYROR50rZQERERkVzk7u7O22+/zapVq/D19aVp06YULFiQ8+fPs2fPHgoXLsykSZPS1KlSpQqXL19m5MiRODs706hRI+rXr288SPydd97Bzc2NmJgYtm3bhpOTE71792by5MksXbqU+/fv884772Q51ipVqrB06VIGDx7M9OnTWbFiBe7u7pQtW5aEhARCQkL4/fffuXfvHt7e3kyaNOmx5zJlZNCgQRw6dIgZM2bwxx9/UKVKFcLCwtixYwdt2rRh2bJlacoXLlyYiRMn8umnn9KrVy+8vb159dVXuXnzJtu3b+fGjRu8++67vPrqq0/t+/XXX6dt27asXbsWHx8fmjRpQvHixbl79y779+/nzJkzNG7cOMO3lmakTp06HDx4kB49elCrVi3u3bvHrl27iI6Opl27dhlulW3Xrh27du0iNDSU1157LUurhZ6XrM5PBwcH3nrrLX799VfatWtHy5YtMRgMHDt2jJs3b9KgQYN0q8HatGnDypUrWbVqFXfu3DF+79u2baNPnz7MmTMnTfnixYszatQoRo0aRZcuXfD19aVw4cIcOXKEgwcPUrVqVbp27WosX6VKFfbu3cvUqVM5fPgwNWrUeGri8u233yYlJYX/+7//Y8iQIfj7+1O/fn0KFy5MREQEBw4c4K+//qJUqVLMnj3b+F2ZmprSpk0bfvrpJ3r06GE8wD8wMJAHDx4wbdo0evTowd69e/n222/x9vbG3t4+w99pd3d3RowYQVBQEGvWrOHixYs0atSI5ORkjh49ypEjR3j11VfTJLD79OnD9u3bWbNmDRERETg4OBAZGcmmTZvo378/U6dOTTPOokWLMm7cOEaMGEHXrl3x8vKibNmyhIWFsX37dpKTk5k4cWKWz0pr3LgxxYoVM66sywuJYhGR50nJNREREZFcNn78eBwcHFi9ejU///wzCQkJlCxZko4dO9K3b1/Kli2bpvzQoUO5fv0658+fJyIigjp16mBubs78+fOZMmUKx44d4/vvv8fW1paePXvSo0cPYmNjCQwM5NixY6xZs4ZOnTplK9YaNWqwbds2fvnlF3bt2kVAQABRUVGYm5tTsmRJvLy8aNu2LXXq1Mly2zVr1mTx4sXMnDmTgIAAdu/eTaVKlRg5ciTVq1dPl1wD8Pb2pnz58ixcuJD9+/ezefNm8ufPT7Vq1Rg2bFiW3k74f//3f9SpU4f169ezefNmYmJisLKy4rXXXmPkyJF07tw5020VKVKE2bNnM23aNH7++Weio6MpXbo0H374IX379s2wjru7O8WLF+fmzZt5KhmR1fk5depUXn31VTZu3MjChQspVKgQDRo0YPr06cZVeY+qWbMms2bNYs6cOezatYvAwECqVavGvHnzANIl1+Dhirry5cuzYMECNm7cyL179yhTpgx9+/alb9++aVauvffee5w/f57jx4+zfv16ypUrl6lxd+7cGQ8PD5YvX87vv//OunXriI2NpUCBAlSpUoXevXvTunVrrKys0tQbOXIkBQsWZPv27SxatIjixYvTtGlTBgwYQOHChenWrRvr1q1j1apVODs7Y29vn+HvNDxMJK5evZpFixaxY8cO5s+fj8FgoHz58vTp04f33nsvzVl4lStXZsmSJXzzzTccO3aMkydP8sYbbzBv3jwKFy6cLrkGD89IK1euHAsWLGDXrl3cvXuXQoUKUb9+fXr37o2jo2OmntejzMzMaN26NT/88AOVK1emZs2aWW5DRORlYmLIiVf2iIiIiIjIM+vcuTPBwcHs2bPH+MIGkZxw6tQpOnbsSJUqVTLcZp3TVq9ezahRoxg+fDi9evV67v2JiOQmnbkmIiIiIpIHnDlzhuPHj/PWW28psSbZcuvWLX7//fcM30qaeq18+fIvJJb//e9/5M+f33j+mojIv5mSayIiIiIiuSwuLo4xY8ZgYmKiVT6Sbbt37+a9995j3LhxaV5scu/ePX788UcAPDw8nnscCxYs4MKFC7Rv355ChQo99/5ERHKbtoWKiIiIiOSSPXv2EBwczObNm/nrr7949913GTFiRG6HJS+puLg4evTowcmTJ3n99ddp0qQJ8fHx/Prrr4SFheHo6Mj//vc/zM3Nc7zvq1evsnnzZk6dOsXOnTuxtbVl7dq1vPLKKznel4hIXqPkmoiIiIhILhkzZgyrVq2iVKlSdOnShb59+2JiYpLbYclLLDY2lsWLF7N9+3bCwsJISUnBzs4OT09PevfuTf78+Z9Lv8eOHaNbt25YWVnRoEEDRo0aRenSpZ9LXyIieY2SayIiIiIiIiIiItmkM9dERERERERERESySck1ERERERERERGRbFJyTUREREREREREJJuUXBMREREREREREckmJddERERERERERESySck1ERERERERERGRbFJyTUREREREREREJJuUXBMREREREREREckmJddERERERERERESySck1ERERERERERGRbFJyTUREREREREREJJuUXBMREREREREREckmJddERERERERERESySck1ERERERERERGRbFJyTUREREREREREJJuUXBMREREREREREckmJddERERERERERESySck1ERERERERERGRbFJyTUREREREREREJJuUXBMREREREREREckmJddERERERERERESySck1ERERERERERGRbFJyTUREREREREREJJuUXBMREREREREREckmJddERERERERERESySck1ERERERERERGRbFJyTUREREREREREJJuUXBMREREREREREckmJddERERERERERESyySy3AxARyQyDwcDt2/dISTHkdiiSR+XLZ0LRogU0T+SJNE8kMzRPJDM0TyQzNE8kMzRP8q4SJQpmqpySayLyUug4YWVuhyAiIiIiIiLPwL9fy9wO4bnQtlAREREREREREZFsUnJNBAgLC8Pe3p5Lly7lSHsNGjRg7dq1L7zfESNGMHTo0Bxp61n78vDwYMWKFS8kFhEREREREZHcouSayEssOjqa1atX51h7a9as4fbt2znWnoiIiIiIiMi/nZJrIi+xgwcP5lhyLTk5mcmTJxMVFZUj7YmIiIiIiIj8Fyi5JvKI4OBgWrZsiaOjIz169CAiIgKAAwcO8Pbbb+Po6EjDhg2ZM2eOsU5SUhITJkzAxcWFhg0bZivZ9bh+ATZs2IC3tzeOjo54eHiwfPlyALZu3cpHH31EUFAQNWrUIDQ01Fhn5syZuLi44OTkxOLFizMVQ926dbl79y6+vr7Mnj37iX2nMhgMTJw4EScnJxo3bsz//ve/DNtOSUlh5syZNGvWDAcHB9q1a8exY8ey8ohERERERERE8iQl10Qe8dNPP/H9998TEBBAcnIyo0ePJjw8nP79+9O5c2eOHj3KggULWLlyJRs3bgTg559/Ztu2bSxfvpzt27dz+vRpYmJinrlfgNDQUIYPH86oUaM4fvw4kyZNYsKECZw/fx4vLy/69etHzZo1CQ4OxtbWFniYCLS1teX333/no48+YurUqdy6deupMaxfv974vwMHDnxi36kCAwOpXLky+/fvZ+TIkUycOJGgoKB0bS9ZsoTNmzezYMECjhw5gp+fH/369eP+/ftZek4iIiIiIiIieY2SayKP6Nq1K2XLlqVQoUL07NmT/fv3s2nTJqpUqYKfnx+mpqbY29vTqVMnYzJqx44dtGrVisqVK2Ntbc3gwYNJSkp65n6TkpIoX748Bw8epH79+piYmFCvXj2KFSvGmTNnHttW+fLladOmDRYWFvj4+JCUlMSVK1ey/Cwy03fJkiXp3LkzFhYWvPXWW1SrVo3AwMB0ba1Zs4aePXtSsWJFLCws6N69O6+88goBAQFZjktEREREREQkLzHL7QBE8pLKlSsbf7azsyMxMZG///6b4OBgatSoYbxnMBioVKkSABERETRu3Nh4r2jRohQqVOiZ+7116xalSpVixYoVrFmzhhs3bmAwGEhISCAhIeGxbZUvX974s5WVFcATyz+OiYnJU/t+7bXX0tSxs7NLs6U11ZUrV5g0aRJffvml8VpKSgrXr1/PclwiIiIiIiIieYmSayKPyJfv/y/mNBgMwMMz1dzd3Zk3b16GdRISEtKtVEtJSXnmfi0tLVm9ejXff/89/v7+ODs7Y2pqiru7+xPbMjExyVLfj5OZvh+NOzV2S0vLdG1ZWVkxceJEPD09cyQ2ERERERERkbxC20JFHnH58mXjz6GhoVhZWfHmm29y8eJFY9ILIDIy0riCq2TJkoSHhxvv3bhxgzt37jxzv4ULFyY4OBgnJydcXV0xNTUlMjKSGzduZHd4WZKZvh+NGx6uUCtZsmS6tmxtbblw4UKaa2FhYTkftIiIiIiIiMgLpuSayCOWLVtGZGQkd+/eZcmSJTRr1gwfHx+io6Px9/cnLi6O0NBQevXqxZIlSwBo2LAhmzZt4q+//iI2NpZvv/02w9VbWe0XoFy5coSEhBATE8PVq1eZOHEiZcuWNW69tLS0JDIykujo6Gxt/XxU6hbS1HE8rW94mCD75ZdfSExMZNeuXVy4cIHmzZuna7tTp04sW7aMkydPkpyczJYtW2jZsiXXrl17pphFREREREREcpu2hYo8olOnTvTo0YPr169Tu3ZtRo4cSZEiRfD39+err75i3rx5FC1aFF9fX3r16gVAz549CQ0NpWPHjlhYWDBo0CCOHTv2zP0CdO7cmcOHD+Pu7k65cuUYN24cp0+fZvr06ZQoUYJmzZqxfPlyGjduzKJFi55p7MWLF8fT05PBgwfTqVMnBg0a9MS+ATw9PTl16hQTJ06kYMGCjB8/3ngW3aPat2/P9evXGThwILGxsbz66qvMnj2bsmXLPlPMIiIiIiIiIrnNxPDoXjcRkTwsKuoeSUlZO89O/jvMzPJRpEgBzRN5Is0TyQzNE8kMzRPJDM0TyQzNk7yrRImCmSqnbaEiIiIiIiIiIiLZpG2hIs+Rk5MT8fHxj72/bds2ypUr99zjuHnzJk2aNHlimeDg4Oceh4iIiIiIiMi/jZJrIs/R0aNHczsE4OF5akqeiYiIiIiIiOQ8JddE5KXQYfyK3A5BREREJNf592uZ2yGIiMg/6Mw1kUyyt7cnMDDwubTt4eHBihUZJ4+6d+/OtGnTstXu2rVradCgwbOEJiIiIiIiIiJPoOSaSB4TGhrKtm3bcjuMHPHDDz+QlJSU22GIiIiIiIiIPDdKronkMb/++ivbt2/P7TCe2e3bt5kyZQrJycm5HYqIiIiIiIjIc6PkmkgWREZG0qNHD2rWrIm3tzcXL1403jtw4ABvv/02jo6ONGzYkDlz5hjvGQwGpk2bhru7O46OjrRp04YjR46ka3/hwoVMmzaNbdu2UaNGDWNiKjk5mTFjxlC7dm3q1avHli1bshT3zz//TKNGjahbty6jR48mISHBeO/HH3/Ey8sLBwcHfHx82Llzp/He7du3GTRoEPXq1cPJyYk+ffpw/fp1AMLCwrC3t+fSpUvG8tOmTaN79+7cvHmTRo0aYTAYcHJyYvbs2bz++utcuHAhTVzNmjVj1apVWRqLiIiIiIiISF6i5JpIFqxatYpx48axf/9+ihcvzjfffANAeHg4/fv3p3Pnzhw9epQFCxawcuVKNm7cCMD69etZt24dq1at4ujRozRt2pRBgwalW9XVu3dvfH19adGiBcHBwZiamgKwadMmmjdvzsGDB+nQoQPjxo3L9HbLO3fucOLECbZs2cLy5cvZtWsXS5cuBR6ukps9ezZTp07l2LFjDB48mCFDhnDt2jUApk6dyr1799i1axe//fYbAF9++eVT+yxevDgLFy4EHr4xdeDAgTg7OxufB8C5c+cIDw+nRYsWmRqHiIiIiIiISF6k5JpIFvj6+lKpUiVsbGzw8PDg8uXLwMPkV5UqVfDz88PU1BR7e3s6derE+vXrAWjVqhVbt26ldOnSmJqa4uPjw+3bt41JrKepXbs2DRs2xMLCghYtWhATE8Pt27czVTchIYFBgwZhY2PDa6+9RsuWLY2JsjVr1tC+fXuqV6+OmZkZb731FnXq1GHTpk0AfPHFF8yaNQtra2sKFChAs2bNOH36dFYfGwB+fn5s3rwZg8EAPEzsubu7U6hQoWy1JyIiIiIiIpIXmOV2ACIvk/Llyxt/trS0JDExEYArV64QHBxMjRo1jPcNBgOVKlUC4MGDB3z55ZcEBgYSExNjLPPo9sys9JuVuoUKFaJkyZLGz3Z2dsbk2pUrV9i3bx9LlixJE/drr70GwN9//83kyZMJCgoiLi6OlJQUChcunKl+/8nT05MJEyZw9OhRnJ2d2bFjBwMHDsxWWyIiIiIiIiJ5hZJrIllgYmKS4XUrKyvc3d2ZN29ehve/+OILLly4wLJly6hQoQKhoaE0b978mfvNTl2DwYCFhYUx7o8//phevXqlq5eSkkLfvn2pU6cO27dvp2jRoqxevZrp06c/tq8nvbzAxsaGpk2bsnHjRkqUKEF4eDhNmjTJ3qBERERERERE8ghtCxXJAXZ2dly8eNG45REevvwgdXVZUFAQrVu3pmLFipiYmHDmzJkXFts/t5BeuXKFUqVKGeP+50sGrl27hsFg4ObNm1y9epXu3btTtGhRAM6ePWssl7qCLi4uzngtNDT0ibH4+fmxY8cONm3axFtvvWVsQ0RERERERORlpeSaSA7w8fEhOjoaf39/4uLiCA0NpVevXsbtluXLlyc4OJiEhAROnjzJ5s2bAbhx40a6tiwtLbl+/Tp37tzJ9EsLnsTCwoLZs2cTFxdHSEgIW7ZsMa6ae/vtt9myZQsBAQEkJSVx8OBBWrZsyalTpyhatCjW1tacPHmS+Ph4Nm7cyLlz54iNjeXevXsULVqUggUL8uuvv5KcnMzevXs5efKksV8rKysALl++zP379wGoX78+pqam/PDDD7Rq1eqZxyYiIiIiIiKS25RcE8kBRYoUwd/fn127duHs7Ey3bt1o0qSJcbvlxx9/zKVLl6hbty7ffvsto0ePpnnz5vTv3z/dKrZWrVpx+fJlmjRpkmHyLatKlChBtWrVaNasGZ07d8bT05N27doB0KBBA4YPH8748eOpXbs248ePZ9y4cdSqVQszMzPGjRvH999/T/369Tly5AizZs2idOnSvPXWW5iamjJ27Fh++eUXnJycWLduHV27djX2W61aNRwdHWnfvj0rVqwAwNTUlFatWmFtbY2Li8szj01EREREREQkt5kYHt3HJiLynA0fPpwyZcowZMiQLNXrMH7F8wlIRERE5CXi369lbocgWWBmlo8iRQoQFXWPpKSU3A5H8ijNk7yrRImCmSqnFxqIyAuza9cuAgIC2LRpU5brrh7TWX/YyBPpLyWSGZonkhmaJ5IZmiciIpJKyTWRl1RQUFCabZj/VLZsWbZv3/4CI3qyFi1akJCQwFdffUWJEiVyOxwRERERERGRHKHkmshLqmbNmgQHB+d2GJm2bdu23A5BREREREREJMcpuSYiLwWduSYiIpKzdHaXiIhIztDbQkVERERERERERLJJyTWRfzh48CCNGjXC29s7x9uuUaMG+/bty/F2c0JgYCD29va5HYaIiIiIiIjIS0XbQkX+YcmSJdSqVYvp06fneNuPnpF25swZYmJiqF+/fo73IyIiIiIiIiIvhlauifxDbGwsdnZ25Mv3fH89fv75Z/bv3/9c+xARERERERGR50vJNZFHdOvWjSNHjrBo0SI8PT2xt7cnPj7eeH/o0KGMGDECgLVr19KyZUsmT55MrVq1iIiIYMSIEUyYMIH/+7//o27duri6ujJ//nxjfXt7ewIDA5kwYQLLly9n0aJFNG/ePM29VCtWrMDDwwOAsLAw7O3tWb58OXXr1mXTpk0AbNmyBV9fX2rVqkXTpk1ZtWpVpsf6119/0alTJxwdHenQoQN///13mvvnz5+nR48eODk54erqysSJE0lMTDTeX79+PZ6enjg6OtKpUyfOnTtnvLdz505at25NrVq18PDwYOnSpcZ7I0aM4PPPP6d79+60bKmDlEVEREREROTlpuSayCN+/PFHnJ2d6dWrF+PHj39q+Rs3bmBpacmRI0coVaoUAJs2beL1119n3759fPrpp3z77bfcuHEjTb3Ro0cb+9mxY0em4zt8+DC7d+/Gx8eH4OBgPv/8cz799FOOHTvGlClTmDx5MsePH89UWyNGjKBcuXLs27ePyZMnp0nMPXjwgPfee4/69euzf/9+Vq9ezaFDh1i4cCEAp0+fZty4cXzxxRccPnwYNzc3+vfvT3JyMufPn2fw4MEMGjSII0eOMGnSJL7++mt+++03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pMef9yv/bZonkhmaJ3lXiRIFM1VObwsVkZfC6jGd9YeNPJH+UiKZoXkimaF5IiIiIlmh5JpINt28eZMmTZo8sUxwcPALikZEREREREREcoOSa/JS+N///pfbIaRTvHhxJc9ERERERERE/uOUXBORl4LOXBMRyX06s0tEREQkPb0tVOQlNmvWLDp27JgjbXXv3p1p06blSFsiIiIiIiIi/xVKronkQb/++it///13bochIiIiIiIiIk+h5JpIHjRz5kwl10REREREREReAkquieQxrVu35o8//qB///589tlnnD9/nh49euDk5ISrqysTJ04kMTExw7oHDhzg7bffxtHRkYYNGzJnzhzjvREjRvDZZ58xfvx4ateujaurK8uXL09TPzk5mTFjxlC7dm3q1avHli1bjPfCw8Pp168fLi4u1KlTh6FDhxIdHQ3AoUOHqFOnDoGBgbRo0YJatWrRu3dvYmJiOHr0KNWrVycqKsrYVlxcHI6OjuzduzcHn5yIiIiIiIjIi6fkmkges2HDBgD8/f0ZM2YM7733HvXr12f//v2sXr2aQ4cOsXDhwnT1wsPD6d+/P507d+bo0aMsWLCAlStXsnHjRmOZbdu28frrr3Pw4EEmTpzI+PHjOX/+vPH+pk2baN68OQcPHqRDhw6MGzeOpKQkAPr370/BggXZtWsX27dv58aNG4wdO9ZY98GDB2zevJlVq1axbds2Lly4wE8//USdOnUoVaoU27ZtM5bdu3cvBQoUoF69ejn+/EREREREREReJCXXRPKwgIAADAYDffv2xcLCAltbW3r37s369evTld20aRNVqlTBz88PU1NT7O3t6dSpU5qyZcuWpWPHjlhYWNCsWTOqVavGnj17jPdr165Nw4YNsbCwoEWLFsTExHD79m3OnTvHmTNn+PTTT7GxsaF48eK8//777Nq1i4SEBODhqrf33nuPQoUKUbp0aerUqUNISAgmJib4+vqmSfL9+uuveHt7Y2pq+hyfnoiIiIiIiMjzZ5bbAYjI44WGhnLr1i1q1KhhvGYwGLCwsEhX9sqVKwQHB6crW6lSJePnR3+Gh8m2GzduGD+XL1/e+LOlpSUACQkJhIWFUahQIUqUKGG8b2dnR2JiIhERERnWz58/P3FxcQD4+fkxd+5crl69SsmSJQkICMhw9Z2IiIiIiIjIy0bJNZE8zNLS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6ZKmLTOztP8KsbKyYuLEiXh6emY4hgkTJvDee++xc+dOtm3bxvz58/npp5+wtbXNsLyIiIiIiIhIXqdtoSK5xM7OjpCQkDTXQkJCjIkmCwsLHjx4YLx35cqVNGWjo6MpVaoUXbt25YcffqBFixasX7+ecuXKkS9fvjQvLUhMTCQiIsLYrqOjI9u3b+f+/ftUqFABR0dHjh8/bjxvDSAoKIhKlSrh7e2Nubk58fHxXLp06YljsrW1TdMvPFyhBw9XsN25c4cKFSrQu3dvfvrpJ1577TV27NiRlccmIiIiIiIikqcouSaSS7y8vAgNDWXVqlUkJSURFBTEL7/8YnxTZ8WKFTl16hTh4eHcvXuXRYsWYWpqCsCJEyfw8vIiKCgIg8HArVu3uHz5MnZ2dhQsWBBvb2+mTZtGeHg4cXFxfPPNN/Tq1QuDwQCAq6srS5YsoU6dOgBUrlyZyMhI9u/fb0yulStXjvDwcK5fv87NmzcZN24cJUuWNCbpMtKpUyeWLVvGyZMnSU5OZsuWLbRs2ZJr166xZcsWOnToYEwoXr16lYiICOzs7J7bMxYRERERERF53rQtVCSXlCtXjtmzZzNjxgwmT55MyZIlGTx4sPGstPbt27N//35atGhByZIlGTVqFDt37gTA0dGRfv36MWTIEG7evEnhwoXx8vKia9euAIwePZoJEybg4+NDvnz5qFWrFv7+/sYtpy4uLnz77bfGbZ4mJiY4ODhw7NgxatasCYCnpye7du3C29ubokWLMmzYMBo2bMjnn3/O1KlT050Xlxrz9evXGThwILGxsbz66qvMnj2bsmXLUqZMGf744w969OjBnTt3KF68OB06dKBZs2bP+1GLiIiIiIiIPDcmhtSlLCIieViH8StyOwSR/yT/fi1zO4QcZWaWjyJFChAVdY+kpJTcDkfyKM0TyQzNE8kMzRPJDM2TvKtEiYKZKqeVayLyUlg9prP+sJEn0l9KREREREQkN+jMNRERERERERERkWxSck1ERERERERERCSbtC1URF4KOnNN5P/7t52DJiIiIiLyMtPKNRERERERERERkWxSck1Eclx0dDSrV6/O7TBEREREREREnjsl10Qkxx08eFDJNREREREREflPUHJNRB4rODiYLl264OTkRP369Rk7diyJiYmsXbuWBg0apCnbsWNHZs2axdatW/noo48I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eHg4J06coF69enh5efHTTz8xadIkzM3N8fDwMNb18vLim2++ISIigtq1a5v0rGFhYdStW5f27dtTp04d1qxZw7Rp0yhWrBj//e9/eemllwgODsbd3Z0+ffrQr18/qlWrZtoEERERERERESmCzAy37rMTKcKysrKwsrIyJr0GDhxIXl4eo0aNMpbf+pKBBg0aEBYWRuvWre/ZtsFgICcnBysrK+DGWzPHjx/Pr7/++gieRB5E6+FzCzuEf11kj+aFHcJjxdLSnNKli5OWlkFOzu1nFYqA5omYRvNETKF5IqbQPBFTaJ4UXeXLm3Y+uF5oII+Fq1evUrduXT788EPatWvHoUOHWLduHcOGDQNg586dvPvuu/z444/83//9HzExMaSkpODj42NS+507d6Z8+fKEh4dz5coVfv75Z+rXr/8In0ju14Ih7fTHRkRERERERIocrVyTx8bmzZuJiIjgr7/+okyZMrRq1YoePXoYV7LNmjWL2bNnc+HCBZycnOjduzeNGjUyqe3ExESGDRvGvn37sLGxoW7dunz66ac888wzd70vPDyc+fPn37G8R48ehIWFmf6QcldKrsnd6P/jJ6bQPBFTaJ6IKTRPxBSaJ2IKzZOiy9SVa0quichjQ39s5G70f5SIKTRPxBSaJ2IKzRMxheaJmELzpOjStlAReaI8bWeu6bw1ERERERGRx4PeFioiIiIiIiIiIvKAlFwTeQDTp0/H09OTYcOGcfXqVd555x3c3NzYvXs3jRs3ZsGCBY88hiVLluDt7U3Xrl0fetvJycm4urpy/Pjxh962iIiIiIiIyJNE20JFHsDkyZPp06cPISEhrFmzhr179/Lrr79SpkwZVq1a9a/EMG3aNN58800GDhz40Nt2cHAgPj7e+H3btm3Y29vj6ur60PsSEREREREReZxp5ZrIA0hPT6dy5crGz8888wxlypT512Nwdnb+V/qaNWsWBw4c+Ff6EhEREREREXmcKLkmcgdnzpyhR48e1KlTh1q1atG3b19SU1ONq7fCwsJwcXHhs88+M17fuXMnAQEBzJ174/D93NxcIiIi8PX1xcvLi969e3Px4kUA8vLyGD9+PI0aNcLNzY233nqL3bt3mxRbQEAAycnJjBgxgtDQUKKjo/H19c1Xp02bNkyYMAGACRMm0K1bN/r06UPNmjUBCAkJYcqUKfTv35+aNWtSt25dYmJiAEhKSsLFxYVjx47RvXt3YmNjGTFiBJ06dcpXdlNERAQhISEAxMXF4eHhwaxZs6hZsyZ79+4F4KeffqJp06a4ubkRGBjI2rVrH+RnERERERERESlSlFwTuYOwsDBKlCjBunXrWLVqFefOnSM8PNy4XTIyMpIjR44QHh5OuXLliI+Px8vLK18bP/74I2vWrCEqKorY2FiuXbtGeHg4AD/88APLli1j+vTp7Ny5k+DgYHr06MHVq1fvGdv69etxcHDgs88+Y+bMmSY9z759+6hduzY7d+40XpszZw4tWrQgLi6ONm3aMHz4cLKzs/PdN2XKFGNfP/zwg0l9ZWdnc+LECbZu3Yq7uzurV69m4sSJjBo1it27d9O7d2/69OnDqVOnTGpPREREREREpKhSck2kAIcOHeLgwYP0798fe3t7ypUrx3vvvce6devIysoyuZ3o6GjatWuHo6MjxYsXZ/DgwbzxxhsALFy4kM6dO1OlShWsra0JCQnhmWeeITY29pE8k4WFBe3atcPCwsJ4zcPDg7p162JlZUXTpk1JT0/n3Llz/7iv7Oxs2rdvj62tLWZmZixcuJBWrVrxyiuvYGlpyeuvv06tWrVYunTpP+5LREREREREpDDphQYiBUhKSqJkyZKUL1/eeM3Z2Zns7GzOnj1rcjuJiYk4Ojoavzs5OeHk5ATAyZMnGTlyJF988YWxPC8vj9OnTz+EJ7hdxYoVMTMzy3ft1thsbW0ByMzMxMbG5h/3V6lSJePnkydPsmXLlnwr3wwGA//5z3/+cT8iIiIiIiIihUnJNZEC3G112t8TVHdjZmZGXl5egWW2traMGDGCxo0b33d8psjNzc333dLy9n/czc0fzuLVv/f19/5sbW356KOPCA0NfSj9iYiIiIiIiBQV2hYqUgAnJycuXbpEamqq8VpCQgI2NjZUqFDhvto5fvy48fuJEyeYM2eOsezIkSP56iclJT1QvDY2Nly7ds34PTc3l+Tk5Adqy5S+4MYKt5sSExPveo+zs/Ntz3rq1CkMBsPDD1BERERERETkX6TkmkgBXF1dqVq1KqNHj+bq1aucPXuWyZMnExgYiJWVlcntvPXWW8ydO5eEhAQyMjIYNWoUu3btAqBt27bMmTOHffv2kZuby/Lly2nevPkDHfJfuXJlMjIy2Lx5M1lZWXz33XcPNXFlY2PDyZMnuXLlCmXKlKFEiRKsXr2a3NxcNm/ezL59++56/9tvv83y5cuJjY0lJyeH7du307x5c3777beHFqOIiIiIiIhIYdC2UJECmJmZERkZSXh4OP7+/hQrVoxGjRrRr1+/+2onJCSECxcu0K5dOwwGAz4+PgwePBiAVq1acfr0aXr27El6ejovvPACEydOzHdWmaleeeUVOnfuTN++fbGwsCA0NBQPD4/7budO2rRpw9ixY9m6dSsxMTEMHTqUUaNGMXv2bBo2bEiHDh3YunXrHe/39fVl4MCBDB8+nNTUVBwdHRk2bBju7u4PLUYRERERERGRwmBm0L4sEXlMpKVlkJNT8Bl2IpaW5pQuXVzzRO5K80RMoXkiptA8EVNonogpNE+KrvLlS5hUT9tCRUREREREREREHpC2hYoUMampqTRo0OCudeLj4/+laERERERERETkbpRcEyliypUrp+RZAVoPn1vYITywyB7NCzsEEREREREReUS0LVRE7mj79u3Uq1ePZs2aPdR2r1+/jouLC3FxcQ+1XREREREREZF/m5JrInJHP/zwA+7u7ixdurSwQxEREREREREpkpRcE5E7Sk9Px9nZGXNz/U+FiIiIiIiISEH0b8wiUqCOHTuyc+dOZs6cSePGjfnjjz9455138PT0pE6dOgwdOpTr168b669du5YWLVrg7u5OQEAAs2fPNpZdvXqVDz/8EE9PTxo1asT69esL45FEREREREREHjol10SkQD/99BNeXl6EhoayZMkSQkNDcXNzY/PmzSxYsICdO3cybtw4AA4fPkzv3r3p1asXO3fuZOTIkYwePZpff/0VgClTpnD48GGWLVvGwoULWblyZWE+moiIiIiIiMhDo+SaiNzTxo0buXbtGh988AG2trY4OzvToUMHVqxYAcAvv/yCj48PjRo1wsrKCh8fH/z9/Vm+fDkAa9asoV27dlSoUIFSpUrRtWvXwnwcERERERERkYdGyTURuaekpCScnJywtrY2XqtcuTKnTp0iLy+PpKQkqlatmu+eypUrk5ycDMCZM2dwdHQ0llWpUuVfiVtERERERETkUVNyTUTuKSsrq8DrZmZmJpVnZ2eTm5trvG4wGB5yhCIiIiIiIiKFQ8k1EbknJycnEhMT8yXREhIScHR0xNzcHGdnZxISEvLdk5CQgJOTEwDPPvssp0+f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Wg+fW9ghGEX2aF7YIUgBLC3NKV26OGlpGeTkmHamoTx9NE/EFJonYgrNEzGF5omYQvOk6CpfvoRJ9bRyTUQeCwuGtNMfGxERERERESlylFwTeQKFh4czf/78O5b36NHjX4xGRERERERE5MmlbaEi8tjQyjW5Gy2nF1NonogpNE/EFJonYgrNEzGF5knRpW2hIvJEKQpnrumsNREREREREfk788IOQERERERERERE5HGl5JrIfXJxcWHjxo2FHUahOnr0KI0bN8bd3b2wQxEREREREREpVEquich9mz9/Ps888wy7du16oPsvXrzIggULHnJUIiIiIiIiIv8+JddE5L5lZGTg6OiIpeWDHdu4fft2JddERERERETkiaDkmsgDSElJoVOnTtSoUYNmzZpx9OhRY9muXbto06YNHh4e+Pn58e2335KXd+ONLxMmTKB79+5MmDABLy8v/Pz8WLt2LdHR0dSvXx8vLy8mT55sbOvixYv069cPPz8/PDw86NGjB2fPnjU5zpiYGBo3boyHhwdt27bl0KFDxrK1a9fSokUL3N3dCQgIYPbs2cayQYMGER4ezpdffknt2rXx9vZm2rRpAAwYMIBFixaxcuVKXF1dAThz5gw9evSgTp061KpVi759+3Lx4kUA4uLi8PDwYNasWdSsWZNJkybx4Ycfsn//flxdXUlMTLz/H0BERERERESkiFByTeQBREVFMWzYMLZu3Uq5cuUYM2YMAKmpqXTp0oWgoCDi4uKYOnUqCxcuZO7c//+my71791KuXDm2bNlCgwYNGDZsGPHx8axevZpPP/2UCRMmcP78eeBGkiszM5Nly5axadMm7Ozs+Pjjj02K8cCBAwwbNozPP/+cHTt24OfnR1hYGLm5uRw+fJjevXvTq1cvdu7cyciRIxk9ejS//vqr8f6lS5fy8ssvs2XLFvr378+3337LuXPn+OabbwgKCqJJkybEx8cDEBYWRokSJVi3bh2rVq3i3LlzDB061NhWdnY2J06cYOvWrYSFhdGjRw9q1KhBfHw8Tk5O//j3EBERERERESksSq6JPICgoCCef/557O3tCQgI4Pjx48CNhFSlSpXo0KED1tbWVK9enaCgIFasWGG818rKinbt2mFtbU39+vVJSUnhvffew8bGhoCAAHJzc0lMTOT8+fNs2LCBvn37UrJkSezt7enXrx9b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H0+hQoWM5W+88QaLFy8mJiaGGzduMGbMGPbv329s+/z581y7do3MzEyTdv39/Vm0aBGnTp0iPT2d6dOnG08UFREREREREfmr0rJQ+UspX748kydPZsKECXz99deUKVOGfv36mZW0up/hw4cTEhJCq1atsLS0xM3NjalTp5p1MEDVqlUJDQ0lJCSEy5cv8/LLLzNt2jSsra1xd3c3nhA6cOBAHB0dCQ0NxcvL65HttmrVit9++4133nmHa9euUapUKdq1a0fTpk0B6NChA//5z3/46aef+OSTT+65v0mTJvj5+dGhQwfs7e0ZMGAA+/btM5Z37dqVy5cv07FjR3JycqhTpw7Dhw8H4LXXXmPjxo34+vqyZs0ak3YDAwO5cuUK3bt359q1a1StWpX58+dTpEiRRz6TiIiIiIiIyIvKIsecKTgiIvnAlSs3yMzU6aJyfwUKWFK8eCGNE3kojRMxh8aJmEPjRMyhcSLm0DjJv0qXLmxWPS0LFREREREREREReUxaFiryGDZs2MCQIUMeWO7p6cmcOXOeYUQiIiIiIiIi8jwouSbyGFq0aEGLFi2edxh/K+0+X/xc+58a3Pq59i8iIiIiIiL5k5aFynO1d+9eGjRoQMuWLZ96266uruzevfupt/s4XFxciIiIAMDPz4+wsLBH3hMYGMj48ePzODIREREREREReRKauSbP1bfffoubm1ueJJGio6ONn48ePUpycjJ169Z96v3k1qZNm8yqp2WlIiIiIiIiIvmfZq7Jc5WSkoKzszOWlnk7FL///nt++umnPO1DRERERERERP5+lFyT56ZLly5ERUUxZ84c/Pz8cHFxIS0tzVg+YMAAhg4dCsCKFSto3bo1X3/9NW5ubiQmJjJ06FBCQkL46quv8PLyonbt2sycOdN4/52lmCEhISxatIg5c+bQrFkzk7I7Fi9eTOPGjQGIi4vDxcWFRYsW4eXlxdq1awFYv349/v7+uLm50aRJE5YuXfpYz924cWMWL17MokWLjH3ecezYMapWrUpiYiJdu3YlNDQUgEmTJhEcHMzMmTOpV68enp6ejBo1ynjf5cuXeeedd6hevTr+/v78+OOPuLi4EBcX98h4IiMjcXd3Z968edSsWZODBw8CsGTJElq0aEGNGjVo3rw569evN96TlpbGqFGjaNSoETVq1KBz584cP37cWO7i4sK6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el577TWioqJwdXWlevXqVK9enVq1auHg4JDXMYrkC4cPH6ZSpUq0bNkSa2tr0tLSOHXqlLH86tWrWFtb06RJE0JCQpg2bRpLlizJdT/Ozs7ExMQYv2dmZnL27FmcnJye+BkeN8aSJUtSqFAhk7iSk5O5dOkSzs7OODs7c/PmTZPDEVJSUrhy5QoAN27cICsri7p16zJs2DDCwsLYtGmTsVxERERERETkRWVWcq1169Zs2rSJ9957j19//dX459ixYyazXkT+ysqXL09CQgLnz58nKSmJkSNHUqZMGRITEwHo0KEDM2fOJC0tjYyMDH755RcqVKiQ6378/f1ZtGgRp06dIj09nenTp5OVlUXjxo2f+BkeN0ZLS0tat27NjBkzSEhI4ObNm4SGhuLk5IS7uzv//Oc/cXd354svvuDy5ctcu3aNESNGMGTIEADef/99Ro8eTUpKCtnZ2Rw8eJBixYpRtGjRJ34mERERERERkecpV2vL+vbty++//05UVBRRUVHs3r2bjh075lVsIvmKn58fDRo0oGXLlrz11ls0atSI4OBgtm7dypgxYxg/fjzbt2+ndu3a1K1blz179hAaGprrfgIDA2nevDndu3enbt26REZGMn/+fIoUKfLEz/AkMQ4dOpSqVavSrl07fH19uXjxInPnzsXKygqAsWPHkpOTQ5MmTWjWrBlZWVl8/fXXAISEhHD27FkaNGiAp6cnCxYsYMqUKY+9vFVEREREREQkv7DIycnJMbfy6NGj2bZtG5cvX8bR0ZH4+Hj+/e9/07t377yMUUQEgCtXbpCZ+ehTUeXvqUABS4oXL6RxIg+lcSLm0DgRc2iciDk0TsQcGif5V+nShc2ql6tpIz///DObN2+matWqrFy5khkzZpCVlfVYAYqIiIiIiIiIiLzoCuSmsp2dHQAZGRkAuLu7M378+KcelIjk3oYNG4x7nN2Pp6cnc+bMeYYRiYiIiIiIiPz15Sq5VqJECVasWEG1atUYPHgw//jHP7h06VJexSYiudCiRQtatGjxvMMQERERERER+VvJVXLt66+/5uLFi7Rq1Ypvv/2WCxcuMHbs2LyKTUTEqN3ni595n1ODWz/zPkVEREREROTFYnZy7cKFC5QpUwZHR0cAunXrxqVLl3jppZfyLDgREREREREREZH8zKwDDfbv30+bNm24fv268VpMTAxd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LiIiIiIiIvLYcjVz7fz589SqVYtatWoZryUkJODg4PDUAxORF8uAAQN4/fXX+e6770hMTKRDhw784x//4J///CcZGRmcPXuWn376CRsbG7Kzs9m5cyfLli173mGLiIiIiIiIPJFcJdfat29v/JyRkcH169epWLEi69evf+qBiciLZeXKlRgMBqysrHBwcMDT05MjR44Yk2udOnXC1tb2eYcpIiIiIiIi8lTlKrm2a9cuk+9Hjhxh48aNTzUgEXkx7d27lylTpnDmzBkyMzPJzMykefPmxnLNcBUREREREZG/olztufZnr7zyCocPH35asYjIC+rUqVP069ePNm3asGfPHqKjo2ndurVJnQIFcpXLFxEREREREXkh5Opfu0uXLjX5/scff3DhwoWnGpCIvHiOHz+OwWDg7bffBiAnJ4fjx4/zf//3f885MhEREREREZG8lavk2qFDh0y+Fy1alIkTJz7NeETkBVS+fHlSU1M5fvw4Dg4O/Pe//8VgMHDhwgVycnLuqW9jY8PFixe5evUqBQsWxGAwPIeoRURERERERJ5crpJrX331VV7FISIvMHd3dzp37kyXLl2ws7MjODiYjz/+mODgYAYOHHhP/aZNm7Jo0SIaNWrEnDlzqFmz5nOIWkREREREROTJmZVca9y4MRYWFg8s37Zt21MLSEReTMOGDWPYsGEm16Kiou5bt3LlyuzYseMZRCUiIiIiIiKSt8xKrs2aNQuA5cuXU6xYMerWrUt2djYRERFkZmbmaYAiIgBhn3bkypUbZGZmP+9QRERERERERIzMSq5VrlwZgBMnTjB79mzj9erVq9OrV6+8iUxERERERERERCSfs8xN5QsXLvD7778bv586dYq4uLinHpSIiIiIiIiIiMiLIFcHGgwcOJB3332XGzduYGFhgY2NDcOHD8+r2EREjNp9vviZ9jc1uPUz7U9EREREREReTLlKrvn6+uLr68vVq1fJycmhePHieRWXyN+ei4sLM2fOpEGDBs81jsaNG9O9e3c6duz4XOMQERERERERyY9ylVy7dOkSEyZMIDo6GgsLC9zd3enbty/FihXLo/BE5HEsX76cxo0bU6JEiecdioiIiIiIiMhfWq72XBs+fDgVKlQgJCSEzz77jFKlSjFs2LC8ik1EHkNWVhZff/01V65ced6hiIiIiIiIiPzl5Sq5duPG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30/79u1xd3fHx8eHcePGkZ19e2PJSZMmERwczMyZM6lXrx6enp6MGjXKrHf4+uuv89tvv9G7d28++ugjAH777TfefvttPDw88Pb2ZsSIEaSlpRnv2bp1q/EZGjdubHzvf/agd5lbdy/1vHXrFv369aN69er4+fmxZ88e/vWvfxEZGWmsf+PGDd5//33c3Nzw9fU1lnl5eXH9+nX8/f2ZPHkyt27d4sMPP6ROnTq4u7vToUMHjhw5kuv4RERERERERPITJdfEbH369KFKlSr89NNPTJ06lfHjx7N792569+5N4cKF2bZtG5s2beLChQuMGDHCeN+tW7dYt24dS5cuZePGjZw4cYJly5YBEBISQs2aNdm7dy9bt24lMzOTadOmERQUhL+/P82bNyc6OhorKysA1q1bxxdffMF///vfR8abmJhI37596dWrF1FRUbzzzju89957FChQgNmzZwO3k2ht27Y1uS8pKcnYf2RkJDNmzGD58uUme4sdOHCAzMxMtm/fzsSJE/nuu+84fPjwI2NavXo1cHuPt6+++or09HQCAwOpUaMGu3btIiwsjKioKCZMmADAr7/+Sr9+/Xj//feJioriiy++YOzYsfz444/3tP2gd/kkxo4dy4kTJ9i8eTPfffcdM2fONC6lvWP58uW8++67REZG4uHhYUw0rlq1yvi/ffr04dtvvyUpKYktW7YQGRlJ/fr1GT58+BPFJyIiIiIiIvK8KbkmZjl27BgnTpzgvffew87OjqpVqzJ58mQKFizI0aNHGTx4MPb29pQqVYoePXqwbds20tPTgdvLA999912KFi1KuXLlqFWrFjExMQBcu3YNW1tbChQoQNGiRZk6dSoff/zxA+OoXr061atXx8LC4pExb9iwAScnJ1q2bIm1tTVt27YlJCTEOAPtQdauXYuDgwOdO3fGYDBQrVo1/P392bBhg7GOlZUVPXv2xGAwUKdOHUqUKGEyg85cERER3Lp1i759+2Jra4uzszOdO3c29vX9999Tp04dmjZtirW1NXXq1KFRo0asX7/+nrZy+y7Nja9Dhw6UK1eOMmXKEBgYeE+dxo0bU716dWxsbHj11Vc5ffr0fdu6du0a1tbW2NraYjAY6N27NytWrHii+ERERERERESeNyXXxCznzp3D3t6eYsWKGa/VrVuXpKQkihYtSunSpY3XnZ2dycjI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B/4fO3aMy5cv061bN2xsbKhQoQL16tXLtk5AQABFixalYMGCeHp6PrKf9PR0PvjgAwoUKECxYsWoVKkSZ8+eBeD777+nYcOGvPPOO7z22mt8/PHH3L59+7HxPsyMGTMYNmwY1tbW2NvbU6NGjSfaIpicnEzv3r3Jmzcv77zzDs7OzkacW7duzfK8Dzucv0aNGpQsWRILCwv8/f05evQoFy5cAOCHH37A0tLygVVbD/P999/j6emJm5sbefPm5dNPP82y0qxLly4sWrSIggULYm1tTYMGDfjpp59IS0t7aCy7du0ib968tG3bFmtra2rVqoWbm5tRduXKldSuXRtPT0+srKxwc3PDx8cny7xycHCgadOm5M6dG19fX9LT0/n111/NHtsnYWVlRUBAAFZWVsa1eys1c+fOjY+PD0lJSU+dhL1famoqbdq0wdbWFgsLC5YvX07z5s159913yZUrF++99x6VKlVi3bp1f7ovERERERERkZcp18sOIDsTJkxgz549WVafPcqFCxews7OjYMGCxrVq1aplKePg4GB8trGxMVboXLhwgejoaMqVK2fcz8zMNA5zByhevDiWlv/LRebJk+eBLYAPEx8fz2uvvUb+/PmNa6VKlcq2zv1x5smTJ8uWy8eVvRdTQkICtWrVMu7dSyo+jWPHjjFu3DhOnTpFamoq6enpvPvuu2bXL1SoUJa+748zPj4+yzM8bGxKlChhfHZ0dKRixYqsWbOGHj16sHXrVnx8fMiV6/FTOSEhIcsZZfnz58/S37Vr1xgxYgQ//PADycnJwN0EZnp6utH+/bHEx8fz5ptvZpkXpUqVMlbDXbhwgb179z4wrzw9PY3vf/z9ALPm1dMoVqwYFhYWWa7d37+tra3Rv42NzZ/ur3jx4sbnCxcusHv37iwr3zIzM/nHP/7xp/sREREREREReZlydHItPj4eJycnpkyZ8sD2vD+ytLQkIyMj2zJ/TCzcY2trS61atZg+fXq27T8Nk8lEenp6lmtPG+eTxJWRkUHu3LnNKpudxMREOnfuTEBAADNnzsTOzs5Iej7KH583u37vJevuyczMfKDM/Sut4O4bVsPCwujevTvh4eFMnDjRrGfJyMh4IAl3f2x9+vTBxsaG1atXU6xYMfbu3UvHjh0fGcvjfltbW1sCAgIYPHjwI2N62nlljj/G9rAE5LPq/499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xMeOUUhICAsXLiQsLIx69eoBkJiYyKeffoqnpyeurq507tyZ2NhYo87PP//M+++/j5ubG1WqVGHo0KFGnPd71Fg+zrfffsvYsWPZtGkT5cqVIz09nTt37jBixAhq165NhQoVaNu2LSdPnjTqZDc+98vIyGDUqFF4enri4uJC48aN2blz52NjEhEREREREcnplFyTZ65Hjx6ULl2aPXv2EBoayoQJE9i9ezfBwcHkz5+fbdu2sXnzZi5fvszQoUMBmDt3LleuXGHr1q1ERUVRo0YNBg8eTPny5QkJCeGNN94gOjqaqlWrAnDkyBEqV67M/v37/1RMa9asASA0NJQvv/zygXrZxQx3E1nr169nyZIlbNq0iVOnTrF06dLHxjN48GDc3d0JDAxk69atAAwaNIiEhATWrFnDzp07sbW1pXfv3gCYTCYCAwOpUKECu3btYtmyZezfv5+JEyc+0PajxvJxgoKC8Pf3p0GDBkRHR2NlZcX48ePZv38/8+fPJyoqirJly9KlSxfjTLrHjc8969evZ8+ePaxZs4aDBw/SoUMH+vXrR2pq6mPjEhEREREREcnJlFyTZ+rEiROcOnWK7t27kydPHsqUKcOUKVPImzcvx48fp2/fvtjZ2fHGG2/QuXNntm3bhslk4ubNm+TOnRtbW1usra0JDg5m5cqVj+zHysqKgIAArKysnjqmYsWKZVvv5MmT2cYMd8+D++CDDyhQoADFihWjUqVKnD179skGDbhx4wZbt26ld+/e2NvbY2dnR8+ePYmOjiYmJobIyEhu377Nhx9+iK2tLU5OTrRt25aNGzc+0NaTjmV2li9fTpcuXXBwcDCSfQkJCRw6dMis8bk/ply5cpEnTx6srKz497//za5du8idO/dTxSUiIiIiIiKSUyi5Js/UhQsXsLOzo2DBgsa1atWqceXKFQoUKEDhwoWN605OTqSmpnLp0iXatGnDuXPnqFWrFv3792fbtm3Z9lOsWDEsLCz+VEylS5fOtl5sbGy2Md/j4OBgfM6TJw8pKSlmxXW/ixcvkpmZmSUmJycnAOLi4oiNjcXR0THLixZKlizJxYsXycjIyNLWk47loyQmJnLr1i3efvtt41q+fPl4/fXXjZjMGR8APz8/cuXKRc2aNenduzerVq0iPT39qeISERERERERyUmUXJNnytLS8oFkD/DASqb7WVhY4ODgwIYNGxgzZgx2dnYMGTKEXr16PbJOrly5so3j/hgeFdPjPC7m+9v/sx7X16PuPyzB+KRj+axjelhcBQsWZOnSpXzzzTc4OjoyadIk2rVrR1pa2hPHJSIiIiIiIpKTKLkmz5SjoyPJyclcvnzZuBYeHk7hwoVJTEzkypUrxvWzZ89iY2ND0aJFSU5OJj09nWrVqjFo0CCWLVvG5s2buX79uln9WltbZ1kxduHChcfG9MMPPzz2WbKL+VlydHQ02r+/L7i7GszR0ZGYmJgsCa2zZ8/i4ODwQHLvz47lPa+//jr58uXLElNiYiJXr141YjJ3fO7cucPt27epWLEiH3/8MevWreP06dP89NNPTxSTiIiIiIiISE6j5Jo8U2XKlKFs2bJMmDCB5ORkTp8+zcCBA7l9+zalS5dm3Lhx/P7771y6dIlp06bh5+dH7ty56dmzJ6NHjyYpKYmMjAwOHz5MwYIFKVCgALa2tty6dYtLly49cstlqVKliIiIICUlhfPnz7N27drHxnSvLRsbG86fP09SUlKWNsuVK5dtzH+WjY0NsbGxJCYm8vrrr+Pp6cnEiRO5ceMGiYmJTJgwgSpVqvDmm29Ss2ZNcuXKxdSpUzGZTJw9e5Z58+bRpEmTB9rNbizNiem3337j5s2bZGRk0LBhQ2bMmEF8fDy///47Y8eOxdHREVdX1ycan5EjR9KvXz+uXbtGZmYmx48fJyMjg+LFi//pcRQRERERERF5mZRck2du+vTpxMXFUa1aNbp27UpwcDC1atUiNDSUy5cvU7t2bVq2bEmFChUYMmQIACEhIZw/f56aNWvi7u7O/PnzmTp1KpaWllStWhUHBwfq1q3L9u3bH9pn7969uXbtGlWqVKFfv34EBQU9NqaaNWsC0Lp1a7766iv69u2bpY6FhUW2Mf9ZzZo1IzIykvfee4/09HRGjx5N3rx58fHxwdfXFzs7O+NtoPny5WPGjBns378fDw8POnXqhL+/P127dn2g3ezG8nEaNWrEuXPn8PLy4vLly/Tv358yZcrQokULvLy8SEhIYPbs2VhZWT3R+Hz88cdYWlpSv359KlasyMiRIxk3bhz29vZ/fiBFREREREREXiKLzMzMzJcdhIiIOa5fTyYt7cnPz5O/h1y5LClUKJ/miWRL80TMoXki5tA8EXNonog5NE9yrsKF85tVTivXREREREREREREnlL2r1wUkafStWtXdu/e/cj7ISEhDz0v7XkKCQlh6dKlj7zfrVs3goODX2BEIiIiIiIiIq8+bQsVkVdCi+GLnrpuaLeGzzASyam0nF7MoXki5tA8EXNonog5NE/EHJonOZe2hYqIiIiIiIiIiDxnSq7JK2/fvn3UrFkTX1/fZ952uXLlst3e+SI5OzsTGRn5zNpr2bIlkydPfmbtiYiIiIiIiPwd6cw1eeXNnTsXFxcXJkyY8Mzbjo6ONj4fP36cxMREqlWr9sz7EREREREREZFXk1auySsvKSkJJycnLC2f73ResWIFe/bsea59iIiIiIiIiMirRck1eaW1a9eO/fv3ExYWRv369XF2dubOnTvG/T59+tC/f38AVq5cScOGDRk1ahQuLi5cunSJ/v37ExISwpdffknlypWpWrUqM2fONOrf24oZEhLCwoULCQsLo169elnu3bNo0SK8vb0BiI2NxdnZmYULF1K5cmXWrVsHwIYNG/D398fFxYU6deqwZMmSJ3remJgYWrVqhYuLC82bN+eXX34x7v3000906NABNzc3qlatyogRI0hNTTXuT506FU9PT6pUqcLUqVOztNu/f38GDhxI+/btadjw7uH/iYmJfPrpp3h6euLq6krnzp2JjY016vz888+8//77uLm5UaVKFYYOHWqM/cqVK2nUqBFLliyhevXqVK5cmYULF/L999/z3nvvUbFiRYYOHfpEzy4iIiIiIiKSEym5Jq+0+fPn4+7uTmBgIMOHD39s+cuXL2NjY8P+/fspWrQoAOvWreNf//oXu3fvpm/fvowfP57Lly9nqTd48GCjn61bt5od3w8//MD27dvx8/MjOjqagQMH0rdvXw4ePMjo0aMZNWoUhw4dMru9hQsXMmLECHbv3o2TkxO9evUC4Pbt23zwwQdUq1aNPXv2sGzZMqKiovj2228B2LVrFzNmzGDixIlERkaSmZnJ6dOns7S9bds2AgMDWbt2LQCDBg0iISGBNWvWsHPnTmxtbenduzcAJpOJwMBAKlSowK5du1i2bBn79+9n4sSJRntxcXFcunSJHTt20LFjR8aMGcPatWv573//y/Tp01m8eDHHjh0z+9lFREREREREciIl1+Rv5datW3Tq1IncuXMb1xwcHGjatCm5c+fG19eX9PR0fv3112fSX5MmTbCzs8PC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i927d9O3b1/Gjx/P5cuXmT59OiVKlGDQoEHMnTv3oXW//fZbevToQVRUFJUrV+aLL74A4PLly3z44Yd07NiRqKgoKlWqlCWmJ3X48GHeeOMNdu/ejZeXF8OGDTOeeeDAgUyePJmrV68CMGjQIIoUKcLOnTvZuHEj586dIzQ01Ky4oqOjGThwIH379uXgwYOMHj2aUaNGcejQoaeOXURERERERCSnUHJNnqu8efMSGRnJv//9bywsLHB2dsbZ2TnLtkhLS0u6d++Ora0tbm5u1KhRg8jIyAfaWr58Oc2bN+fdd98lV65cvPfee1SqVIl169Y9UDYpKYmMjAzy5s0LwLvvvsvevXspW7asWXHfuXOH3r17kydPHkqXLo2fnx8RERHGfSsrKwICArCysnpofQcHB5o2bUru3Lnx9fUlPT2dX3/91ay+vby8KF++PNbW1tSvX59ff/2VjIwM9u3bR968eWnfvj3W1tY0b96ct99+26w2HyZ37twEBARgbW1NrVq1SEhIoHPnztjY2ODt7U16ejoxMTEAzJgxg2HDhmFtbY29vT01atQwfsPHxbVy5Upq166Np6cnVlZWuLm54ePjw+rVq586dhEREREREZGcQi80kOdu48aNzJkzh7i4ODIyMkhNTcXNzc247+TkhLW1dZbvp06deqCdCxcusHv37iwrvjIzM/nHP/7xQNnSpUvj7++Pj48PlStXxtPTk6ZNm1KoUCGzYi5QoAD29vbG9+LFi2fZnlmsWDEsLCweWd/BwcH4nCdPHgBSUlLM6vv+ura2tqSnp5OamkpCQgLFihXLktB79913HzpW5ihWrJjx+d74Fy1aFAAbGxvgbpIR4NixY4wbN45Tp06RmppKeno67777LsBj47pw4QJ79+6lXLlyxv3MzEw8PT2fKm4RERERERGRnETJNXmu9u7dy7Bhwxg7diz16tUjd+7ctGnTJkuZPyapMjMzsyTb7rG1teXjjz8mMDDwsf1aWFgQEhLCBx98QHh4OJs2bWLmzJksXboUR0fHx9ZPT09/IKb748yVK/u/OpaWT78o9FF1MzIyHuj3WffzsGuJiYl07tyZgIAAZs6ciZ2dHRMmTDBeHvG4uGxtbQkICGDw4MFPHauIiIiIiIhITqVtofJcHT16lLfeegtfX19y587NnTt3jMP774mNjSU1NdX4fuHCBWMF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V+nTpw+1a9fG09OTLl26cP78eZPf56effiI0NBQ3NzeaNWvGr7/+aixfvHgx/v7+vP3223zxxRfk5pr/EMo/H82MjY3FxcUF+P+/7/r16wkKCqJatWq0b9+eS5cumfSxb98+goKCqFq1Kl26dOH69evGsoULF9KkSROqV69O48aNWbNmTZ5xHDp0iNatW+Pu7k7NmjUZMmQI6enpea7JlJQUBgwYgLe3N+7u7nTv3p0LFy6YxHxnTf7444+89dZbnDhxwmS8hg0bPtK6FBERERERESmIlFwz0/fff4+XlxdhYWGMGDHiofUvXryInZ0de/bsoVSpUgCsWrWKt956i+3bt/PJJ5/w7bffcvHiRZN2w4YNM46zYcMGs+P75Zdf2Lx5M0FBQcTFxTFkyBA++eQT9u3bx9dff81XX33F/v37ze5v/vz5jBgxgk2bNpGQkMD7779PixYt2LVrF+XKlWPChAnA7WOegwYNYujQoezfv59Ro0YRERHB8ePHadKkCd27d6datWrExcXRpUsXgoODady4MXFxcVhZWQGwevVqRo0axXfffYfBYKBHjx689tprxMTEsG7dOi5cuMDXX38N3D6ae/nyZTZs2MDu3bupV68ew4YNA2DcuHEULVqU2NhYtm3bhrOzs7Hdw4wePZobN26wadMmfv75ZwC+/PJLkzrTp09n1KhR7Ny5k5IlS/Ltt98CcPr0aT7//HM+++wzdu7cyT//+U9jH0/K999/z8yZM9m6dSsWFhaEh4eblK9atYoFCxawdu1ajhw5wtKlSwHYvHkzo0ePJiIigr1799KnTx8++eSTexJdAAMHDqRVq1bs27ePlStXcuLECRYtWpTnmhw8eDDp6emsXr2arVu34uDgwKeffmrS3501GRISgpeXFytXrjSWHTt2jKSkJBo3bvxE75OIiIiIiIjIs6bk2lNy/fp1unTpgo2NjfFa2bJleffdd7GxsSEwMJCcnBx+//33JzJeSEgIjo6OWFhYEB0dja+vL97e3lhZWeHp6UmTJk1Yvny52f35+vpSsWJFXnnlFapVq0a5cuWoW7cudnZ2eHt7G+MuW7Ysu3btok6dOlhYWFC7dm1efvlljh49avZY1apVo1q1alhYWBAXF8f//vc/PvnkEwoVKsTLL79M7969WbFiBQaDgdTUVGxsbLC3t8fW1pYePXoQHR0NYCyztbXFwcGB8PBwYxLwYb744guioqJwcHCgcOHCNGzY0GR3HkBwcDCvv/46hQoVwt/fn1OnTgGwceNGqlSpQsOGDbG1teW9996jXLlyZs/fHO3ataNUqVIULVqUTp06ERsba7I7LiwsjCJFilCuXDnc3Nw4c+YMAEuXLqVp06Z4enoa113lypXzPJqbmpqKg4MDlpaWlCxZksWLF9OxY8d76l25coUtW7bQr18/ihYtiqOjIwMGDGD79u0mO+ruXpMhISGsXr0ag8EA3D4e7OPjQ9GiRZ/ofRIRERERERF51qyfdwB/VUWKFMHR0dHkWtmyZY2fCxUqBEB6evoTGa9MmTLGz+fOnWPnzp24uroarxkMBry9vc3ur3Tp0sbPdnZ2JnOxs7MjMzMTAAsLCxYsWMDSpUu5ePEiBoOBzMxMY7k5nJycjJ/j4+PJycmhZs2aJnVycnJITk6mXbt2dO7cGR8fH+rVq0fDhg1p0KABAB988AHdu3dn69ateHt706RJE2rXrm1WDGfPnuWrr77i8OHDpKenk5ubS7FixUzq/Pn3u3Ms+MKFCyZlABUqVDB3+mapWLGi8bOTkxOZmZmkpKTkGZu9vb3x/ickJFCrVi2TvsqXL09iYuI9Y3z88cd89tlnzJgxA29vb4KDg6lUqdI99e4ctQ0JCTG5bmVlxfnz5ylRogRguiYDAgKMu+e8vLzYsGEDvXr1MnP2IiIiIiIiIgWXkmtPSE5Ojsl3a+t7b+2TehFCXs/zunPEEm4nV0JDQ43HJfPjz7HeL/YlS5YwdepUJk2ahJeXF1ZWVvj4+DzSWHfHbmdnh4ODAwcOHMizbokSJVizZg27d+9m8+bNfP7556xYsYLx48fj6urK5s2b2bp1KzExMfTq1YvWrVszaNCgB46fm5tLt27dePvtt1m/fj0lSpRgyZIljB071qSehYVFnu0zMzPJzs6+p8/8yqvt3dfu7P4yN7a85FW/VatWNGzYkM2bN7Np0yZCQkL49ttvadiwoUk9e3t74Paz4YoXL35PPwkJCYDp7+ro6EiDBg1YuXIlr776KklJSfj5+eUZm4iIiIiIiMiLRMdC88HOzg64/XD9O8x9cH5+2NramuxwO3fu3APrOzs73/NMraSkpHsSgE9CXFwcnp6e1KpVCysrKy5dunTPc+QehbOzMzdv3jS5n2lpaSQnJwNw48YNcnJyqFOnDkOHDmXJkiWsX7+e5ORkUlJSsLGxoUGDBkRERDB58mQWLlz40DEvX75MYmIiHTp0MO66uvtlBQ9TsmRJkpKSTK7dOTJqDnN+37uvJSYmYm9vn2di68+cnZ05ffq0ybXTp0/neWw1OTmZ4sWL07JlSyZNmkS3bt2Mz267m5OTE5aWliZrLCsry/hCg/sJCQlhw4YNrFq1infeecf450hERERERETkRabkWj6ULVsWKysr1q9fT3Z2Nj/++KPJmyUfl52dHQkJCVy7dg24fcRw48aNZGdnExcXR0xMzAPbv/fee+zfv58ffviBzMxMjh07RqtWrfJ8ztbjcnJy4vTp01y7do3ExERGjhxJmTJljIkWOzs7Ll26REpKCpmZmdjZ2XH+/HlSU1Pv2e0F8Oabb+Lu7s6oUaO4evUqqampDB8+nIEDBwLQp08fvv76a9LS0sjNzeXAgQMUK1aMokWL0rZtW6ZNm0ZGRgZZWVkcOnSI8uXLP3QOJUqUwMHBgYMHD5KRkcHKlSs5duwYaWlp3Lhx46Ht69evz6+//kpMTAyZmZnMmzfvoYmmu1WoUIGYmBjS09M5e/asyYP/71iwYAGXL18mJSWFOXPm4OPjc9/dancLDg5m5cqVHDx4kKysLKKjo/nf//5HUFCQSb2kpCT8/f3Ztm0bubm5XL9+nZMnT+Ls7AyYrsmXXnqJwMBAIiMjSUpKIj09nW+++YawsLA8d9XdUadOHaysrJg1axbNmjUz+/6IiIiIiIiIFGRKruXDK6+8woABAxg7diy1atXi2LFjBAYGPrH+W7RoQWxsLO+88w45OTl89tlnHDhwAE9PT8aNG0dYWNgD21eqVIkxY8Ywffp0PD096d27N507d36iMd4RGhpK+fLl8fHxoWvXrrRv35727dsza9Ys5s2bR8OGDTEYDPj6+nLkyBGaNWvGmTNn8PPzu+8OtzFjxmAwGGjQoAGNGjUiJyeHr776CoCIiAjOnj1L/fr18fLy4vvvv2fixIlYWloyduxYtmzZQq1atahTpw47d+4kMjLyoXOwtrYmPDycqVOnUqdOHfbs2UNUVBSlS5fmnXfeeWj76tWrM3ToUMLDw6lVqxYnT558pLdg9u3bl6tXr1KzZk0GDRpE586d76nTvHlzOnbsSL169QAYPny4WX0HBQXRrVs3Bg4cSM2aNZk/fz4zZ86855lwpUuXZtSoUYwaNQp3d3caN25M4cKF6dOnD3Dvmhw2bBjly5cnKCiIevXq8dtvvzFp0qQHJvysrKxo1qwZDg4O9zxTT0RERERERORFZWF40FYTEXmuEhISaNCgAWvWrMnz5QIvmkGDBvHaa6/Rt2/fR27basSCh9aZ1L1pPqKSvwpra0uKFy9McvINsrPz/9xD+WvTOhFzaJ2IObROxBxaJ2IOrZOC69VXXzKrnl5oICLPxKZNm4iJiWHVqlX5ar/k81D9ZSMiIiIiIiIFjpJrfzPNmzfnzJkz9y2fOXMmXl5ezzCip+/DDz9k+/bt9y2PiIggJCTkLzd2QdK4cWMyMzP5z3/+w6uvvvq8wxERERERERF5YnQsVEReGNq5Jg+i7fRiDq0TMYfWiZhD60TMoXUi5tA6KbjMPRaqFxqIiIiIiIiIiIjkk46FisgL4WEvNNDLDEREREREROR50M41kXzatWsX9evXJzAwMN99REVF0bp16/uWBwQEsGTJknz3LyIiIiIiIiJPl5JrIvk0Z84c3Nzc8v32S3OsX7+eVq1aPbX+n5dZs2aRnZ39vMMQEREREREReWxKronkU1paGs7Ozlha6o/Ro7h69Spff/01OTk5zzsUERERERERkcemrIBIPrRv3549e/Ywc+ZMAgIC2LZtGy1atMDd3Z169eoxfvx4Y93Lly/Ts2dPatasiYeHB506dSI+Pt6kvwULFuDt7Y2bmxtff/218bq/vz8LFtx+1lhubi4TJ06kUaNGVKtWjXfffZedO3ea1F2yZAldu3bF3d2dhg0bsm3bNrPm86AYBw8ezKeffsqIESPw8PCgVq1azJ8/39g2IyODkSNH4uvrS/Xq1Xn//fc5duyYsdzFxYXZs2fj7e3NhAkTqF+/PgaDAU9PT6Kjox/hrouIiIiIiIgUPEquieTD999/j5eXF2FhYfz444/07t2b0NBQ9u/fz/Tp05k1axabN28GYNy4cRQtWpTY2Fi2bduGs7OzSQLt7NmzXLt2jc2bNzNu3DhmzpzJ0aNH7xlz3rx5LFmyhAkTJrB3716aNWtGjx49uHLlirHOjBkz6NWrF7t376ZGjRp8+eWXZs3nYTGuW7eOt956i127djFy5EhGjBjB8ePHAfj222/Zs2cP33//Pbt376ZKlSp069aNzMxMY/uNGzeybNkyevbsyYwZMwDYu3cvLVq0eIS7LiIiIiIiIlLwKLkm8pgcHByIjY2lZcuWWFhY4OLigouLC0eOHAEgNTUVGxsbbG1tcXBwIDw8nAkTJhjbW1tb07VrV2xtbfHx8cHR0ZEzZ87cM87SpUtp164dLi4u2NraEhYWRqFChYiJiTHW8fPzo1q1atja2hIQEMDvv/9Obm7uQ+fwsBjLlClD69atsbW1pWHDhlSuXJktW7YY4+rWrRtly5bF3t6evn37cunSJfbv329s36RJE1555RUsLCwe+f6KiIiIiIiIFGRKrok8AWvXrqVp06ZUr14dV1dXDh48aNy59cEHH7Bp0yYaNGjA559/zu7du03alilTxuS5bfb29ia7vu5ISEigUqVKJtecnZ1JTEw0fi9btqxJPzk5OWRlZT00/ofFWLFixXtivnjxIteuXeP69eu8/vrrxrLChQvz8ssvm8RVpkyZh8YgIiIiIiIi8iJSck3kMe3cuZPw8HB69erF3r17iYuLw8PDw1ju6urK5s2bGTJkCAaDgV69epkcuTR3N1deCbc/t8/vyxUeFuOfXz5gMBiwsLC4b0x/jsvKyipfcYmIiIiIiIgUdEquiTymw4cPU7FiRQIDA7GxsSEjI4NTp04Zy1NSUrCxsaFBgwZEREQwefJkFi5c+MjjODs7c/r0aeP37Oxszp49S7ly5R57Dg+L8c8vYPjjjz8oXbo0L7/8MoULFzaJ69q1a1y5cgVnZ+fHjktERERERESkoFNyTeQxOTk5kZSUxPnz57l8+TLh4eGULFmSCxcuANC2bVumTZtGRkYGWVlZHDp0iPLlyz/yOMHBwcyfP59Tp06RmZnJlClTyMnJwd/f/7Hn8LAYExMTWbZsGVlZWWzYsIHjx4/j6+uLpaUlTZs2ZerUqSQlJXHz5k0iIyMpV64c7u7ueY5lb28PwJkzZ7h58+Zjxy4iIiIiIiLyPCm5JvKYAgICqF+/PoGBgbRp0wZfX1+6d+/Oxo0bGT16NGPHjmXLli3UqlWLOnXqsHPnTiIjIx95nLCwMBo3bkyXLl2oU6cOu3fvZu7cuRQpUuSx5/CwGOvXr8+BAweoVasWw4YNIzw8nDfffBOAwYMHU7lyZVq1aoWfnx+XLl1i1qxZ9z0KWrlyZdzd3XnvvfdYsGDBY8cuIiIiIiIi8jxZGAwGw/MOQkQKrsGDB5ORkcG33377XONoNeLBibhJ3Zs+o0ikoLK2tqR48cIkJ98gO/vhb8mVvyetEzGH1omYQ+tEzKF1IubQOim4Xn31JbPqWT/lOEREnogln4fqLxsREREREREpcJRcE/mLW7t2LQMHDrxvuZeXFzNnznyGEYmIiIiIiIj8dehYqIi8MLRzTR5E2+nFHFonYg6tEzGH1omYQ+tEzKF1UnDpWKiI/KU86Jlret6aiIiIiIiIPC96W6iIiIiIiIiIiEg+KbkmUoAkJCTg4uLCqVOnnlsMYWFhjB079onVExEREREREfkr07FQETFh7ssN9BIEEREREREREe1cExERERERERERyTcl10QKqHPnztG5c2dq1qxJzZo1+fjjj0lNTTW7/fLlywkICMDd3Z22bdty7NgxAKKiomjdurVJ3bp16xIdHQ1Ahw4diIyMBODMmTN06tQJT09PvLy86NWrF8nJyffUi4qKonv37kybNo26devi5eXFyJEjjf2np6czYsQIfH19cXNzo0OHDvz222/5vzkiIiIiIiIiBYSSayIF1NChQylZsiRbt25l7dq1nDlzhkmTJpnV9siRI4SHh/PFF1/wyy+/4O3tTY8ePcjJyXmkGCIiIvDw8GDXrl1s3LiR7OxsJk+enGfd/fv3k52dzZYtWxg/fjz//e9/OXz4MACRkZH8+uuvLFq0iF27duHq6kqvXr0wGAyPFI+IiIiIiIhIQaNnrokUUFOnTsXCwgJbW1tKlChBvXr12L9/v1ltly1bRq1atahVqxYAnTt3pmLFimRkZDxSDKmpqdjb22NtbU3RokWZNGkSlpZ55+StrKzo1q0blpaW1K5dmxIlSnDq1CmqVq1KdHQ0Y8eOpVSpUgD07duX77//nsOHD1O9evVHiklERERERESkIFFyTaSAOnLkCGPGjOHEiRNkZWWRk5ND1apVzWobHx+Ps7Oz8XuhQoUICgp65Bh69erFJ598wrJly/D29qZp06ZUq1Ytz7plypQxSbwVKlSI9PR0rly5wo0bN+jRowcWFhbG8tzcXM6fP6/kmoiIiIiIiLzQdCxUpABKTU2la9eueHh4EBsbS1xcHF27djW7vYWFxSMdubzfcVFfX19iYmLo1asXV65coX379nz//fd51r3fjjZ7e3sAFi5cSFxcnPGfo0eP0rhxY7NjFBERERER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c+Y8sM/GjRszY8YMDAYDNWrUyLNOy5YtWbBgAadPn+bGjRuMHj2avXv3AtC2bVvjiytycnJYs2YNTZs25Y8//mDNmjW0atXK+Ly5xMRELly4YHL0V0RERERERORFpGOh8lT93//9H3/88QchISGkp6fz2muvMWDAAKpVq8akSZMYOXIkdevWxdHRkQYNGjBo0CAAKleuTGRkJBEREVy9epW33nqLyZMnY2NjQ4MGDQgICKBt27Y4OjrSr18/fvnlF7NjatGiBUOHDuWdd95hx44dWFlZERQUxJdffmn2rjWAgIAANm3aRGBgICVKlGDgwIHUq1ePIUOGMHr0aCpVqvTA9p988gmfffYZjRs3pmjRonz22WfExMSYNXb//v0ZPnw4AQEBZGdnU758ecaMGUOJEiUAmDRpEv/5z3+YMmUKJUqUIDg4mLCwsAf22bhxY6ZNm0b79u3ve6y2Q4cOXL16ldDQUAwGA7Vr12bYsGEAvPfee5w/f55evXqRlpbG66+/zoQJEyhTpgyvvfYa//vf/+jYsSOpqam88sortGrVioYNG5o1XxEREREREZGCysLwKA96EvmLOnfuHCEhIcTGxpq8gEAKjlYjFgAwqXvT5xyJFFTW1pYUL16Y5OQbZGfn/WxAEa0TMYfWiZhD60TMoXUi5tA6KbheffUls+pp55r87V2/fp3hw4cbd8JJwbTk81D9ZSMiIiIiIiIFjpJr8re2cuVKhg0bhr+/P7179zZev3z5Mn5+fg9sGxcX91Riep5ji4iIiIiIiMij0bFQERERERERERGRfNLbQkVERERERERERPJJyTUREREREREREZF8UnJNREREREREREQkn5RcExERERERERERyScl10RERERERERERPJJyTUREREREREREZF8UnJNREREREREREQkn5RcExERERERERERyScl10RERERERERERPJJyTURKdASExPp2rUrNWvWxM/Pj9GjR5Obm/u8w5JnYOvWrdSpU4d+/frdU7ZmzRqaNWuGu7s7LVq0YNu2bcay3Nxcvv32Wxo0aICXlxedO3cmPj7eWJ6SkkLfvn2pU6cO3t7eDBkyhPT09GcyJ3myEhMT6dmzJzVr1qROnToMHjyY1NRUAI4dO0b79u15++23eeedd5g5c6ZJ28dZQ/JiOX78OB07duTtt9+mTp069O3bl0uX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tWrV7lkHR44cMVknd6+DnJwcfv31V6pXr065cuUoWrSoSfnJkyfJzMykatWqT3NK8hSsWLGCK1eu4OfnR82aNWnRogUANWvW5M0339Q6EQB+/fVXvvrqK5Nrp06dwtbWFh8fH60TAaB06dI4Ojpy7Ngx47XExERsbGy0Tv7ilFwTkQKrSpUquLq6MmbMGNLS0jh16hSzZs0iNDT0eYcmz1Hr1q3ZsWMHMTExZGRksHTpUn7//XeaN28OQGhoKHPnzuXUqVOkpaURGRlJ5cqVcXV1pUSJEgQEBDB27FiuXr1KUlISEydO5L333jM+8FxeDNnZ2QwdOpQBAwbg7e1tUubj44OjoyOTJ0/m1q1bHDp0iKVLlxr/3fE4a0heLFWrViUtLY3Ro0dz69Ytrl69SlRUFJ6enoSGhpKYmMiSJUvIyMjg559/5ueff6Z169bA7XWwbNkyDh48yK1bt5g8eTK2trb4+vpiZWVF69atmTJlCufPnyc5OZlvvvmGRo0ambxkQ14MgwcPZv369Sxfvpzly5czdepUAJYvX06zZs20TgS4vcN90aJFTJ06lczMTM6cOcO4ceNo06YNwcHBWicCgLW1Ne+99x5Tpkzh7NmzXLlyhYkTJ9KsWTPeffddrZO/MAuDDu2KSAGWlJTEsGHD+OWXX3B0dKRt27b06tXL5NlJ8tdzJ4lxZ+fRncTXnbc1/vTTT4wZM4bExET+8Y9/MGTIELy8vIDbz6KIiopi4cKF3Lhxg5o1azJixAhKly4NwPXr1xk+fDhbtmzBxsaGpk2bMnjwYGxtbZ/1NOUx7N27l/fffz/P323dunXcuHGD4cOHc+TIEV555RW6dOlCu3btjHUeZw3Ji+XEiROMHDmSw4cP4+DgQK1atRg8eDClSpViz549jBw5klOnTuHk5ET//v155513jG3nz5/P1KlTuXLlCq6uroSHh/Pmm28CkJmZyb///W9Wr15NdnY2fn5+hIeH3/dNx/LiSEhIoEGDBpw4cQJA60SM9uzZw5gxYzhx4gS2tra8++679OvXDzs7O60TMbr798zKyiIgIIBhw4ZRuHBhrZO/MCXXRERERERERERE8knHQkVERERERERERPJJyTUREREREREREZF8UnJNREREREREREQkn5RcExERERERERERyScl10RERERERERERPJJyTURERERERER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"/>
    </div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell jp-MarkdownCell jp-Notebook-cell" id="cell-id=b05c6bc9">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
    </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
    <h4 id="Brief-interpretation">Brief interpretation<a class="anchor-link" href="#Brief-interpretation">¶</a></h4>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell jp-MarkdownCell jp-Notebook-cell" id="cell-id=78bb1ccf">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
    </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
    <p>The top 5 categories hold the vast majority of the orders, indicating a high concentration of demand for these products which are furniture or lifestyle products ranging from health &amp; beauty to tech.</p>
    <p>There is a long tail of products with significantly lower order counts, suggesting the large inventory of products that the store holds.</p>
    <p>Overall, this tells us that the store is known more for its top few products amongst its customer base.</p>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell jp-MarkdownCell jp-Notebook-cell" id="cell-id=d9a3d3e3">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
    </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
    <h3 id="2.3-Box-Plot:-Order-Value-vs-Number-of-Items">2.3 Box Plot: Order Value vs Number of Items<a class="anchor-link" href="#2.3-Box-Plot:-Order-Value-vs-Number-of-Items">¶</a></h3><p>The relationship between physical order volume and gross financial value is evaluated using a distributional lens. By plotting order_total_value against the discrete num_items variable, the workflow identifies how capital allocation shifts as consumers increase their purchase quantity. This visualization is pivotal for detecting price outliers and understanding the variance in spending patterns across different basket sizes.</p>
    </div>
    </div>
    </div>
    </div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=ebec9141">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea">
    <div class="jp-InputPrompt jp-InputArea-prompt">In [ ]:</div>
    <div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
    <div class="cm-editor cm-s-jupyter">
    <div class="highlight hl-python"><pre><span></span><span class="c1"># Configure canvas for distributional bivariate analysis</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">(</span><span class="n">figsize</span><span class="o">=</span><span class="p">(</span><span class="mi">12</span><span class="p">,</span><span class="mi">7</span><span class="p">))</span>

    <span class="c1"># Generate box plot to visualize value distribution and extreme outliers</span>
    <span class="n">sns</span><span class="o">.</span><span class="n">boxplot</span><span class="p">(</span>
        <span class="n">data</span> <span class="o">=</span> <span class="n">df_orders_cleaned</span><span class="p">,</span>
        <span class="n">x</span> <span class="o">=</span> <span class="s1">'num_items'</span><span class="p">,</span>
        <span class="n">y</span> <span class="o">=</span> <span class="s1">'order_total_value'</span><span class="p">,</span>
        <span class="n">color</span><span class="o">=</span><span class="s1">'steelblue'</span>
    <span class="p">)</span>

    <span class="c1"># Enhance aesthetics for professional reporting</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">'Order Total Value Distribution by Number of Items'</span><span class="p">,</span> <span class="n">fontsize</span> <span class="o">=</span> <span class="mi">16</span><span class="p">,</span> <span class="n">pad</span> <span class="o">=</span> <span class="mi">20</span><span class="p">)</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">xlabel</span><span class="p">(</span><span class="s1">'Number of Items in Order'</span><span class="p">,</span> <span class="n">fontsize</span> <span class="o">=</span> <span class="mi">12</span><span class="p">)</span>
    <span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">'Order Total Value ($)'</span><span class="p">,</span> <span class="n">fontsize</span> <span class="o">=</span> <span class="mi">12</span><span class="p">)</span>

    <span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
    </pre></div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell-outputWrapper">
    <div class="jp-Collapser jp-OutputCollapser jp-Cell-outputCollapser">
    </div>
    <div class="jp-OutputArea jp-Cell-outputArea">
    <div class="jp-OutputArea-child">
    <div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
    <div class="jp-RenderedImage jp-OutputArea-output" tabindex="0">
    <img alt="No description has been provided for this image" class="" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAA/MAAAKHCAYAAADNOBjAAAAAOnRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjEwLjAsIGh0dHBzOi8vbWF0cGxvdGxpYi5vcmcvlHJYcgAAAAlwSFlzAAAPYQAAD2EBqD+naQAA+w9JREFUeJzs3XlcVOX+B/DPHGYGZJFFQUXFSsUNMU1ZXFApNOGmuZXdMkNxy9KsbnXTrGu2+Kubt8UsxKhsM3PLlJIERZAlVxARl0xMTUdhZGeWM78/aI4MAwgIzIx83q+XL5lznhme4cxyvud5nu9XZjAYDCAiIiIiIiIimyFYugNERERERERE1DAM5omIiIiIiIhsDIN5IiIiIiIiIhvDYJ6IiIiIiIjIxjCYJyIiIiIiIrIxDOaJiIiIiIiIbAyDeSIiIiIiIiIbw2CeiIiIiIiIyMYwmCciIiIiIiKyMQzmiYiq+PDDD9GrVy98+OGHlu6K1QoNDUWvXr3w559/Wrorkl69eqFXr16W7kaTscTf+M8//0SvXr0QGhpa57aWZE3HNT09Hb169cL06dMt3RWbcbt9nn700UcYOnQo+vbti3nz5lm6O0REkFu6A0REtVGpVNiwYQNSUlLwxx9/oKioCI6OjvD29kZgYCAeeughdO/e3dLdbBINDVgmTpyIt99+u0H32bRpE1xdXXHfffc16H6NodFoEBISgoKCAnzzzTe455576mwviiLuu+8+XLhwAdHR0Rg5cmSz97E5vfTSS9iyZYvJNkEQ4OLiAm9vb/j7+yMiIgKBgYE13n/evHkoKiqCm5tbo/vw+eefo0+fPrX+jurc3NzwwgsvwMXFpdG/s7GOHz+O3bt34+mnnzbZ/sILL7R4X6xNeno6Hn/8cQCVr6vIyMha2xpfd7t370aXLl1aqoutwr59+/Dhhx/CyckJUVFRuOuuu+ps/+eff+Lee++Fm5sb0tPTTfbFx8ejqKgIkyZNas4uE1ErwGCeiKzSd999hzfffBMVFRXw9/fHhAkT4O7ujuLiYmRmZmL9+vX48ssv8cQTT+D555+HnZ2dpbt8S2oKWr799lucP38ekydPNrto0bNnzwY9viiKePvtt3Hvvfe2SDCvVCoxZcoUrF27Ft9///1Ng/l9+/bhwoUL6Nq1K0aMGNHs/Wsp9913HwYNGgQA0Ov1uH79Ok6cOIHNmzdjw4YNCAoKwsqVK9GxY0eT+z300EO39HvVajXefvttLFiwoN7BvLOzM2bNmnVLv7exNm/ejPXr15sF85bqj7X64IMPEBYWxkDdAnJycgAAkyZNwrPPPntLj/Xhhx/C1dWVwTwR3TIG80Rkdb7++mssX74cnp6eWLVqFYYMGWLW5vTp01i0aBE+++wzlJeX49VXX7VAT5tOTUHLnj17cP78eYSFhWH06NG39PgnT55EYWHhLT1GQ02bNg3r1q3Dzz//jCVLlqBt27a1tt2wYYN0H0G4fVaABQcH47HHHjPbnp+fjzfffBPbt2/H448/jm+//Rbt2rVrst978OBBGAyGJnu85nbw4EFLd8Hq9e3bF8ePH8err76KdevWWbo7rU5FRQUAwNXV9ZYep7CwEKdOncLgwYOboltE1MrdPmdMRHRb+Ouvv/DWW29BqVTis88+qzGQB4AePXrgyy+/RPv27fHNN98gIyND2mdc27pw4UIcPXoUEydORP/+/XHy5Empzc6dOzFp0iQMGDAAAQEBmDNnjjTyUpudO3di+vTpGDx4MPz8/BAaGorXXnsNly9fNmlnXGc8adIknD17Fo8++igGDBiAPXv2NP4PU4Pz589j6dKlCA0NhZ+fH+655x5MnToV69evh06nk9pNnz4dEyZMAABs2bLFbN2vXq/HN998g4ceegiDBg1Cv379MGzYMCxcuBDHjx9vdP+6dOmCkSNHory8HFu3bq213eXLl7F3717Y29tj8uTJACpPnD/99FNMmDABAwcORL9+/TBy5Ei8+OKLOH/+fL1+f13rrV966SX06tULX331ldm++h7nW+Hh4YF3330XDzzwAM6dO4d33nnHZH9Na+bLy8vx8ccfS3+T/v37IzQ0FC+88AJOnDhhct8nn3wSQOUa3169euGll14CcGMN81dffYVNmzYhNDQUQ4cOBXDz9fFlZWVYuXKl9HobMWIE/vOf/5hdJJo+fTp69eplNrUYqByBN743q942vs6Mx8z4vGs7hidOnMCzzz6LESNGwM/PD0OGDMFjjz1W4+vM2J+TJ09iz549mDZtGgYNGoSBAwfisccew4EDB2p8vnUpKCjA0qVLpd8fGhqKVatWSQHfpUuX0KdPHwwZMkTaVp3xWKxcubJevzM0NBT33XcfkpOT63w/1fZ7alq3bjzm1Wdv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IFBZaurhhx/Gjh07sHXr1lten+3s7IyPPvoI//vf/7Bz506oVCp4eHhgxowZWLRokVnStw8//BCrV6/G7t27kZSUhD59+ki5EGoK5l955RUsWbIEmZmZyMvLM6tuUFVwcDC+//57REdHIy0tDXFxcXB2doafnx8ef/zxW36uN+Pu7o6PPvoI7777LjZt2gS1Wo2OHTvi6aefxty5c2u8z8iRI9G+fXtcvXq1SUflqz7+P/7xjxrrrzs5OeGzzz7DypUrcfjwYRw/fhxdu3bFggULWiyY79evH5544gmsWrUKX3zxBSoqKtC9e3dERUUhIiLCpO3gwYOxadMmrF27Fvv370diYiIUCgV69uyJZcuW4eGHH641IWNDzJ07Fz169MD69evx008/oaysDB4eHrj//vulfc3B3d0dr7zyCj788EPEx8eblI4LDw9Hly5dsG7dOuzfvx87duxAmzZt0KdPH7zwwgt44IEHmqVPTz31FHr16oXvv/8ev/76K9RqNRQKBe644w4sXLgQM2bMaJJlIUTU9GSGppg7SURERES1euSRR5CVlYXExEQp2RkREdGt4Jp5IiIiomaUnZ2NQ4cOYcyYMQzkiYioyTCYJyIiImom5eXlWLZsWYOqbhAREdUH18wTERERNbHExERkZWVhx44d+OOPPxAZGQk/Pz9Ld4uIiG4jDOaJiIiImlhiYiI2bNiADh06YPHixbUmxyMiImosJsAjIiIiIiIisjFcM09ERERERERkYxjMExEREREREdkYBvNERERERERENobBPBEREREREZGNYTBPREREREREZGMYzBMRERERERHZGAbzRERERERERDaGwTwRERERERGRjWEwT0RERERERGRjGMwTERERERER2RgG80REREREREQ2hsE8ERERERERkY1hME9ERERERERkYxjMExEREREREdkYBvNERERERERENobBPBEREREREZGNYTBPREREREREZGMYzBMRERERERHZGAbzRERERERERDaGwTwRERERERGRjWEwT0RERERERGRjGMwTERERERER2Ri5pTtgzVSqIkt3gYiIiIiIiFoRT0+XerWz+Mj8iRMnMGPGDNxzzz0YOnQonnnmGahUKgBAamoqpkyZgkGDBiEiIgI//vijyX2//PJLjB07FoMGDcIjjzyCY8eOSfsqKiqwbNkyhISE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nGbfygiCgICAYCQlJZplVjbS6XRISkpEQEAwR46IiIiIiIisEIP5VigsbBzU6gLExkbXWCopNjYaanUBwsLGWaiHREREREREVBdms6/D7ZrNHqjMrhwTswZubu4ICRktlUpKSkqEWl2AqKj5TMpERERERETUwuqbzZ7BfB1u52AeqKw3Hx8fh4yMVGg0GiiVSgQEBCMsbBzryxMREREREVkAg/kmcLsH80aiKDK7MhFRCzB+3ioUSggCV7oRERGRufoG88xmT8yuTETUzDgTioiIiJoaR+br0FpG5omIqPmY5yjpAJXqMnOUEBERUY04Mk9ERGRheXnnEBOzBoGBQxEZOQdy+Y2v3fDw8YiNjUZMzBp4e3fhCD0RERE1CBfsERERNZP4+Di4ubmbBfIAIJfLERk5B25u7oiPj7NQD4mIiMhWMZgnIiJqBqIoIiMjFSEho80CeSO5XI6QkNHIyEgFV70RERFRQzCYJyIiagZarQYajQaenh3qbOfp6QWNprItERERUX0xmCciImoGCoUSSqUSKtXlOtupVFegVFa2JSIiIqovBvNERETNQBAEBAQEIykpETqdrsY2Op0OSUmJCAgIhkwma+EeEhERkS1jME9ERNRMwsLGQa0uQGxstFlAr9PpEBsbDbW6AGFh4yzUQyIiIrJVrDNfB9aZJyKiW2VeZ94LKtUV1pknIiKiGtW3zjyD+TowmCcioqaQl3cO8fFxyMhIhUajgVKpREBAMMLCxrG+PBEREZlgMN8EGMwTEVFTEkURWq0GSqU918gTERFRjeobzNdc+JaIiIianCAIsLd3sHQ3iIiI6DbABHhERERERERENobBPBEREREREZGNYTBPREREREREZGMYzBPdZkRRREVFOURRtHRXiIiIiIiomTABHtFtgqWviKyfMZu9QqGEIPB6OhERETUeS9PVgaXpyFakpaUgJmYN3NzcERIyGp6eHaBSXUZSUiLU6gJERc1HUNAwS3eTqNXixTYiIiKqL9aZbwIM5skW5OWdw/LlSxAYOBSRkXMgl9+YcKPT6RAbG4309P1YtuwNBg1EFsCLbUREdbty5TJKS0st3Y0Gc3R0hJdXB0t3g25DrDNP1ErEx8fBzc3dLJAHALlcjsjIOcjNzUF8fBxmzZpnoV4StU55eecQE7Omxott4eHjERsbjZiYNfD27sKLbUTU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KLlDlU2rTeb379+P3NxcZGVlwWg0wmg0YsqUKXjnnXcCMpn3VXMtgA225MKGaURERERETWvfvgNmzJiLzMyV5y2znzFjLtq37yB3qLJROXzZsUlG//3vf/Hmm29i06ZNrvv27duHiRMnYu/evQgPD7/oYxQXV0IQ5C/ZMJkqMG/eLJ821/IlQRDw+utvcF1uPYF8Tnk+iYiIiMhfjh37A199tRE7d+5wldkPHJiO664bhQ4dOsodnk9ER4d5NK7VzsyXlZUhIsI92YiMjAQAlJaWepTMx8SEKWL9RXR0GFatWoXKykq5Q2mW8PBwtGnTRu4wFCWQzynPJxERERH5S3R0T1x2WU+I4rmu9UrI0ZSg1SbzAFo861lSUqWImXkA0OuN0OuNcofRbKWlVXKHoDiBfE55PomIiIhIDtXVgbd7kFRBPzMfExODsrIyt/vKysqgUqkQExPj0WOIogOiGHhl0ERERERERNS6tdo92nr16oUzZ86gpKTEdd/+/fvRpUsXhIV5dqWDiIiIiIiISIlabTJ/6aWXonfv3li6dCkqKytx9OhRZGVl4Y477pA7NCIiIiIiIqIWabXd7AHg7NmzeOKJJ7B7926Eh4fj9ttvxz333ONxw4TCQpOPIyQiIiIiIiI6Jz7es75arTqZbykm80RERERERORPnibzrbbMnoiIiIiIiKi1YjJPREREREREFGCYzBMREREREREFGCbzRERERERERAGGyTwRERERERFRgGEyT0RERERERBRgmMwTERERERERBRgm80REREREREQBhsk8ERERERERUYBhMk9EREREREQUYJjMExEREREREQUYJvNEREREREREAYbJPBEREREREVGAYTJPREREREREFGCYzBMREREREREFGCbzRERERERERAGGyTwRERERERFRgFE5HA6H3EEQERERERERkec4M09EREREREQUYJjMExEREREREQUYJvNEREREREREAYbJPBEREREREVGAYTJPREREREREFGCYzBMREREREREFGCbzRERERERERAGGyTwRERERERFRgGEyT0RERERERBRgmMwTERERERERBRgm80Huu+++Q3p6OhYsWCB3KOQFp06dwrx58zBgwACkp6dj4cKFqKiokDssaqbc3FzcdddduPzyy5Geno77778fhYWFcodFXvDCCy8gNTVV7jCo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fx0rVqxw+/pt27bhzJkzeOedd7BkyRJs3boVs2fPxsGDB5GZmYnFixdj8+bNePfdd13Py/3334+RI0di3bp1+PDDD9GrVy/MmjXL9dx56umnn8bEiROxfv163HbbbXjnnXewcePG847fuXMnunfvfsGqhauvvhpmsxm//PKL677S0lJ8/fXXeO+99zB79mwAwAMPPID9+/fjtddewwcffIC4uDi8+eabbo+1e/duzJ49GwkJCfi///s/vPPOO7BYLPjb3/6GkpISt7FvvPEGXnjhBfz73/+W9BwQEVFgYzJPRERB5ZFHHsHJkyfx/vvvt/ixioqK8Nhjj6FHjx7o27cvRowYgcOHD+P+++9H79690adPH4wYMQI5OTluX1dSUoJ//OMf6NOnD1JTU/H888/DYrHgyy+/BAC8/fbbEAQBy5cvR8+ePZGamooXXngBYWFhePvtt90eKz09Hddeey3atGnTZIz5+flYv3495syZg5tvvhnt27fH0KFDsXDhQhw8eBB79+5FWFgYIiIiAACRkZGIiYnx6Oc3Go3Q6/WuUvawsDD88ssvyM7OxsMPP4zRo0ejffv2uO2223DbbbfhrbfegsVicX29zWbDY489hk6dOmHUqFHo2rUrDh8+jKeffhqdO3fGyJEj0bVrVxw6dAgAkJOTA5vNhltuuQXt2rVD586d8eijj+K9995zxe+p0aNH47rrrkO7du0wd+5caLVa7Nu377zjz549i6SkpAs+ZnJysmusU35+Ph555BGkpqYiKioKx44dw549ezBv3jwMHToUnTp1wrx589CzZ0+3x8rIyEBycjJeeukldOnSBb1798bSpUtRWVmJ//3vf41+lgEDBiA+Pl7Sc0BERIGNyTwREQWVtm3bYubMmVi+fHmjGU6pDAYDLrnkEtftyMhIAECPHj3c7jOZTG5f165dOyQkJLhut2nTBlFRUfjtt98AAPv27UPfvn1hNBpdY/R6Pfr374+DBw+6PVavXr0uGOOBAwfgcDhwxRVXuN3fr18/AHAlyt7inJUePHiw2/2DBg1CVVUV/vjjD9d93bt3h1qtdt2OjIxEx44dERoa6naf8/nr378/YmJi8Le//Q1ZWVnIzc2FWq1Gv379EBYWJinOvn37uj7XaDSIiIhwK+dvSKVSwW63X/AxncsI6pfh6/V6dOvWzXX7yJEjABqft/79+7vd3rdvHwYOHOj2/MTFxbld3HC62P8BIiJqnTRyB0BERORvM2bMwJo1a7B06dJGJfBSGAwGt9vOJK7+/U2tr25qFjk0NNS11rqyshJ5eXmuhNvJYrE0mjWvn/A3pbKysslx4eHhAICqqqoLfr1Uzu93/fXXu93vXI9eWFjoSm7rJ+1A3XN1vucUqLvo8eGHH+LNN9/E22+/jSVLliA5ORlz587FxIkTJcXZ1Pepv6a/oaSkpItuG+c8npKS4rqv4fPufH4afv+GFyMqKyvxySefYMOGDW7319bWQqfTud13sf8DRETUOjGZJyKioKPX67Fw4ULce++9uO2225oc0zCxcyba3tBUAm02m10JXUREBNq0aYPnnnuu0ThBkFZU57xw0LA6wHlbann6xTirE9555x3X5/W1tBQ8JSUFTz31FJ566ikcOXIE7733Hh5//HGkpKRcsAlgS6Wnp+Mf//gHjh07hg4dOjQ5ZuvWrYiIiECfPn3O+zjOJL66utrt/oZVARERERg8eDDuvffeRo/RMJknIqLgxDJ7IiIKSiNGjMCgQYPw3HPPNUrcIyIiGpXg//zzz1773seOHUN+fr7r9smTJ1FeXo6uXbsCqNtG7/fff0fbtm3RoUMH1z+Hw+FWnu+JXr16QRAE/PDDD2737927FwDQu3fvFv407hc+nOXrBQUFbrFHREQgNDS00Yy0FM6dApy6du2KRYsWITw8vMkdA7zplltuQVRUFJ5//vkmy+3z8vLw0UcfYfLkyRdMtjt37gwAjdbn79mzx+32ZZddhqNHj7o9hx06dIDNZuPaeCIiAsBknoiIgthjjz2GgwcPNkrU+/Tpgx9//BFff/01jh8/jrfffrvRWvWWiIqKwt///nccPHgQubm5ePzxx2EwGDBy5EgAddvDVVVV4cEHH8T+/ftx4sQJ/O9//8PNN9+M1atXS/pe8fHxGDduHDIyMvDZZ5/hxIkT+Oabb7B48WIMGDDggrPInoiIiEBhYSH27NmDEydOoFevXhg8eDCeffZZfP311zh58iR2796NGTNmYM6cORcsZb+Yn3/+GXfffTc+/vhjnDhxAidOnMBbb70Fs9mMyy+/vEU/x8VERUXhn//8J3744QdMmTIFW7duxalTp/Drr7/i7bffxqRJk5Ceno45c+Zc8HE6d+6Mnj174o033kB2djZ+++03LF++vNEuBTNmzEBeXh6efvpp5Obm4o8//kBGRgZuvPFGbN261Zc/KhERBQiW2RMRUdDq0qUL7rzzTrzzzjtu98+fP9/VhVytVmPkyJFYsGBBkyXPzdG1a1eMGzcOCxYswOnTp9GxY0esWLHCNePaoUMHvPfee1i2bBkmT54Mq9WKjh074pFHHsEdd9wh+fs9/fTTiImJwcsvv4zCwkJER0djxIgRePDBB1v8s9xxxx3Yvn07pkyZgjvuuAOPPfYYli9fjmXLlmHRokUoKipCZGQkrr32WixYsKDJHgJSvld1dTUyMzOxaNEiaLVadOnSBa+++mqLL0p4Ij09HevXr8eqVavwzDPPoKCgACEhIUhNTcUjjzyCcePGebQM4tVXX8VTTz2F2bNnIzQ0FNdffz3mz5+PRx991DXmiiuuQGZmJpYvX47bbrsNoigiNTUVy5Ytw/Dhw335YxIRUYBQOVpyiZyIiIiIiIiI/I5l9kREREREREQBhsk8ERERERERUYBhMk9EREREREQUYJjMExEREREREQUYJvNEREREREREAYbJPBEREREREVGAYTJPREREREREFGCYzBMREREREREFGCbzRERERERERAGGyTwRERERERFRgGEyT0RERERERBRgmMwTERERERERBZj/D/+LvhBnZ0aNAAAAAElFTkSuQmCC"/>
    </div>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell jp-MarkdownCell jp-Notebook-cell" id="cell-id=d1bb1b4f">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
    </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
    <h4 id="Brief-interpretation">Brief interpretation<a class="anchor-link" href="#Brief-interpretation">¶</a></h4>
    </div>
    </div>
    </div>
    </div>
    <div class="jp-Cell jp-MarkdownCell jp-Notebook-cell" id="cell-id=b0ffa930">
    <div class="jp-Cell-inputWrapper" tabindex="0">
    <div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
    </div>
    <div class="jp-InputArea jp-Cell-inputArea"><div class="jp-InputPrompt jp-InputArea-prompt">
    </div><div class="jp-RenderedHTMLCommon jp-RenderedMarkdown jp-MarkdownOutput" data-mime-type="text/markdown">
    <p>While the total order value generally has a positive correlation with item count, the trend is non-linear. As baskets get larger, we see diminishing marginal returns in total value. This is likely due to a shift in basket composition: bulk buyers often purchase lower-priced 'add-ons' rather than multiplying high-ticket luxury goods, preventing a linear spike in cost.</p>
    <p>Orders with fewer items exhibit the highest variance and extreme right-skewed outliers. This reflects wide variety of products sold in retail behavior. A single item is just as likely to be a high-value electronic (e.g., a laptop) as it is a low-cost consumable (e.g., a pen). As item count increases, the mix of cheap and expensive products naturally averages out the total price, smoothing out the volatility and reducing the range of outliers.</p>
    </div>
    </div>
    </div>
    </div>
    </main>
    </body>
    </html>

</div>