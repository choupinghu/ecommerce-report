---
layout: default
title: Data Preprocessing
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
<h1 id="Data-Preprocessing-and-EDA-for-E%E2%80%91Commerce-Orders">Data Preprocessing and EDA for E‑Commerce Orders<a class="anchor-link" href="#Data-Preprocessing-and-EDA-for-E%E2%80%91Commerce-Orders">¶</a></h1><p>Objective of this section will be to:</p>
<ul>
<li>Load <strong>four tables</strong> (<code>orders</code>, <code>order_items</code>, <code>order_shipping</code>, <code>payments</code>).</li>
<li>Join them into a single order-level dataset.</li>
<li>Clean and transform the data.</li>
<li>Perform basic EDA and visualization.</li>
</ul>
<p>This report outlines the end-to-end pipeline for consolidating fragmented e-commerce tables to analyze order behavior and logistics performance.</p>
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
<div class="jp-InputPrompt jp-InputArea-prompt">In [3]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="kn">import</span><span class="w"> </span><span class="nn">numpy</span><span class="w"> </span><span class="k">as</span><span class="w"> </span><span class="nn">np</span>
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
<h2 id="Part-1:-Data-Preprocessing">Part 1: Data Preprocessing<a class="anchor-link" href="#Part-1:-Data-Preprocessing">¶</a></h2><h3 id="Data-Loading-&amp;-Joining">Data Loading &amp; Joining<a class="anchor-link" href="#Data-Loading-&amp;-Joining">¶</a></h3><p>We first load each table, inspect it, and then join them into a single DataFrame.</p>
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
<h4 id="Load-the-CSV-files">Load the CSV files<a class="anchor-link" href="#Load-the-CSV-files">¶</a></h4><p>In this initial phase, the data foundation is established by ingesting the raw relational datasets. Specifically df_orders, df_order_items, df_shipping, and df_payments. This step ensures that all core entities are correctly mapped into the environment before moving to the integration and transformation stages.</p>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs" id="cell-id=1569a5bf">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [4]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Load the CSV files</span>
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
<div class="jp-InputPrompt jp-InputArea-prompt">In [5]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Execute structural audit for all primary dataframes</span>
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
<h4 id="Join-the-tables-on-order_id-to-create-a-single-order-level-DataFrame">Join the tables on <code>order_id</code> to create a single order-level DataFrame<a class="anchor-link" href="#Join-the-tables-on-order_id-to-create-a-single-order-level-DataFrame">¶</a></h4><p>A unified "Order Analytical Record" (df_orders_full) is constructed by executing a series of inner joins on the order_id primary key. This systematic integration of df_orders, df_order_items, df_shipping, and df_payments ensures that the final dataset contains only synchronized records present across all functional domains, providing a consistent foundation for downstream analysis.</p>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=5403e6e4">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [6]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Consolidate core order metadata with itemized transaction data</span>
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
<h3 id="Data-Cleaning">Data Cleaning<a class="anchor-link" href="#Data-Cleaning">¶</a></h3>
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
<h4 id="Handle-missing-values">Handle missing values<a class="anchor-link" href="#Handle-missing-values">¶</a></h4><p>In this stage, a robust data cleaning pipeline is implemented to ensure the integrity of the df_orders_full dataset. By applying statistical imputation, using medians for numerical features to mitigate outlier influence and modes for categorical attributes, the dataset is standardized for downstream modeling. This phase concludes with a structural filter to remove records with missing primary identifiers or critical payment metadata.</p>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=a7e0967a">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [7]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Handle missing values</span>

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
<pre>Dataframe df_orders_full shape: (99678, 15)
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
<div class="jp-InputPrompt jp-InputArea-prompt">In [8]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Filter invalid numeric records</span>

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
<pre>Dataframe df_orders_full shape: (88853, 15)
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
<div class="jp-InputPrompt jp-InputArea-prompt">In [9]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Ensure zero missingness across all features</span>
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
<pre>There are some null values existing in dataset
[866]
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
<h3 id="Data-Transformation">Data Transformation<a class="anchor-link" href="#Data-Transformation">¶</a></h3><p>Advanced sanity checks are applied to the df_orders_full dataset to ensure internal consistency between interrelated metrics. By enforcing strict logical constraints the data integrity is solidified for downstream feature engineering.</p>
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
<div class="jp-InputPrompt jp-InputArea-prompt">In [10]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Apply logical consistency constraints to ensure transactional integrity</span>

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
<pre>Dataframe df_orders_full shape: (46076, 15)
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
<div class="jp-InputPrompt jp-InputArea-prompt">In [11]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># order_value_per_item: Captures the average economic value of each unit within a basket</span>

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
<pre>Dataframe df_orders_full shape: (46076, 16)
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
<div class="jp-InputPrompt jp-InputArea-prompt">In [12]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Small: 1-2 items | Medium: 3-5 items | Large: &gt;5 items</span>

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
<h4 id="Final-transformation-check">Final transformation check<a class="anchor-link" href="#Final-transformation-check">¶</a></h4><p>A comprehensive state-of-health check is performed on the fully transformed df_orders_full dataset. By verifying the absence of null values across all engineered features and auditing the final schema via info(), the data is certified as "production-ready." This ensures that downstream exploratory analytics and modeling are built upon a clean, high-integrity foundation where all data types and record counts are strictly validated.</p>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=742a2e1e">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [13]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Ensure feature engineering did not introduce missingness</span>
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
<pre>order_id                      0
order_status                  0
order_purchase_hour           0
order_purchase_dayofweek      0
order_purchase_month          0
order_total_value             0
num_items                     0
num_unique_products           0
num_unique_sellers            0
total_item_price              0
avg_item_price                0
total_freight_value           0
top_product_category        523
customer_state                0
payment_type                  0
order_value_per_item          0
order_size_category           0
dtype: int64
&lt;class 'pandas.DataFrame'&gt;
Index: 46076 entries, 0 to 99997
Data columns (total 17 columns):
 #   Column                    Non-Null Count  Dtype  
---  ------                    --------------  -----  
 0   order_id                  46076 non-null  str    
 1   order_status              46076 non-null  str    
 2   order_purchase_hour       46076 non-null  int64  
 3   order_purchase_dayofweek  46076 non-null  int64  
 4   order_purchase_month      46076 non-null  int64  
 5   order_total_value         46076 non-null  float64
 6   num_items                 46076 non-null  int64  
 7   num_unique_products       46076 non-null  int64  
 8   num_unique_sellers        46076 non-null  int64  
 9   total_item_price          46076 non-null  float64
 10  avg_item_price            46076 non-null  float64
 11  total_freight_value       46076 non-null  float64
 12  top_product_category      45553 non-null  str    
 13  customer_state            46076 non-null  str    
 14  payment_type              46076 non-null  str    
 15  order_value_per_item      46076 non-null  float64
 16  order_size_category       46076 non-null  str    
dtypes: float64(5), int64(6), str(6)
memory usage: 6.3 MB
Final Shape of Dataframe df_orders_full (46076, 17)
</pre>
</div>
</div>
<div class="jp-OutputArea-child">
<div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
<div class="jp-RenderedHTMLCommon jp-RenderedHTML jp-OutputArea-output" data-mime-type="text/html" tabindex="0">
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
<hr/>
<h3 id="Data-Storage">Data Storage<a class="anchor-link" href="#Data-Storage">¶</a></h3><p>The refined and validated dataset is persisted to disk. By exporting df_orders_full as a standardized flat file (ecommerce_orders_cleaned.csv), a "Single Source of Truth" is established.</p>
<h4 id="Save-cleaned-dataset">Save cleaned dataset<a class="anchor-link" href="#Save-cleaned-dataset">¶</a></h4>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell jp-mod-noOutputs" id="cell-id=9ac046b6">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [14]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Persist the high-integrity analytical dataset for downstream consumption</span>

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
<h3 id="Load-Transformed-Dataset">Load Transformed Dataset<a class="anchor-link" href="#Load-Transformed-Dataset">¶</a></h3><h4 id="Reload-CSV">Reload CSV<a class="anchor-link" href="#Reload-CSV">¶</a></h4>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=c1b5ae27">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [15]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Load the analytical record</span>

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
</div>
</div>
<div class="jp-OutputArea-child">
<div class="jp-OutputPrompt jp-OutputArea-prompt"></div>
<div class="jp-RenderedText jp-OutputArea-output" data-mime-type="text/plain" tabindex="0">
<pre>Cleaned Dataframe Shape: (46076, 17)
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
<h3 id="Unique-Categories-and-Payment-Types">Unique Categories and Payment Types<a class="anchor-link" href="#Unique-Categories-and-Payment-Types">¶</a></h3><p>A high-level census of the marketplace dimensions is conducted to quantify product diversity and financial channel preferences. By identifying the cardinality of product categories and payment methods, the operational breadth of the platform is established. The subsequent ranking of high-volume categories and dominant payment types provides critical insights into consumer demand and transaction behavior, essential for targeted marketing and payment infrastructure optimization.</p>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=dc776346">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [16]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Quantify categorical cardinality and primary transactional drivers</span>
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
bed_bath_table           5895
health_beauty            4011
furniture_decor          3412
computers_accessories    3386
telephony                2570
Name: count, dtype: int64
--- Top 5 Payment Types ---
payment_type
credit_card    27776
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
<hr/>
<h3 id="Bar-Chart:-Orders-by-Product-Category">Bar Chart: Orders by Product Category<a class="anchor-link" href="#Bar-Chart:-Orders-by-Product-Category">¶</a></h3><p>The transactional volume is visualized across the diverse product landscape to identify primary market drivers. By executing a ranked frequency analysis of the top_product_category attribute, a comprehensive demand profile is established. This visualization is essential for inventory prioritization and understanding which vertical segments contribute most significantly to the platform's order throughput.</p>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=6e622d28">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [17]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Configure visual parameters for executive reporting</span>
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
<img alt="No description has been provided for this image" class="" src="data:image/png;base64,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boUKFez06dOWJ08e97yee+aZZ9y11kT9Crp0L2zYsMEFKGov7dSpU6jPV0GOzjd9+vTuXtC11nmGrfyKLs0Zp0UY9HuSLl06d6/ovldgqs9KAc7TTz/tKig1ni1btrgqSgVA+roW/Z5o/xrrfffdd83X6hqFDZ8UDus+UcWmxqbfl+TJk7v7TOPTl+413bei32mdh66zwmT9rt95552+/elcFPTpHlLolTZtWvv+++/dvGy6x/Vvh3/4p/BW4XfixIldiK3X65gKLr3P1J8+S41FYbc+L/1O6PdO79FxFNK98847bp65yO4XjU/jmj9/vlsoI2wQqn/PFMorBAeABCUEAAAAsebbb78Nueeee0KqVKly1baVK1e6beXKlQv56aeffM9fuHAhpHfv3m5bgwYNQq5cueLb9swzz7jnv/7661D7ql27tnv+yy+/DPX8X3/95Y6tbZ9//rnv+WHDhrnnBg8eHOk5jBgxwr321VdfjfJ5d+nSxb3no48+8j3njUPnpHOUy5cvu+9Llixx26pXrx7yxx9/+N6j61KqVKlwr6F3Ld55552Qixcv+p7funWre0+hQoVCdu/e7Xu+e/fu7vX3339/yMGDB91zurb68s7xgw8+CHWMH3/80e2naNGiIefPn4/0vL1z1DG2bNnie/7QoUO+bQsXLvQ9365dO/fc7NmzQ+1H16d06dIhxYsXDzl37lykx9U+9KXjhOeff/4JeeKJJ9xrunXr5nv+s88+873X/97R56Lros9K215//fVQ11jXpUyZMm6b7mPPhAkT3HONGjUKOXXqlO/5NWvWuOuobfrcwv5+NGnS5JrXc//+/b7n+vfv755r3rx5yL///htqTMWKFQspWLBgyN9//x3q/F555ZWQqBg5cqR7fY8ePUKiY+nSpe79utZnzpwJtW3s2LFu28MPPxzqee++nDVrVqjnvbHXqVMn1Od6+vTpkFatWl31+7tnzx53jXXPbN68OdRn37hxY9/nrGvuefnll91zbdq0CTVeXe9q1aq5bVOmTInS/XL8+HF3fH0GYc990aJF7j29evW67msKAPEdraAAAABxxGtB1AqaarHzqALljTfecFUg27dvd9U/16IKG71flU1qY/SXOXNm14rntZNGhyqO5Pbbb4/ye3RcCa8FtXHjxr4qG1XWeBUwolY9VZ95dF5aNCEsVeKp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AAAAANdCsAZchxUrVrjVNYsVK2Zt2rSxU6dOuec3b95sDRs2tKJFi1qdOnVs6dKlvvdoVdC3337bKlWqZIUKFXLtmZ9++mm4rZsjRoywTZs2ubZTz+7du61JkyZWpEgRq1+/vu3YseO6PrPBgwdbiRIl3PGnTp0aatvMmTPdeIoXL27NmjWzXbt2+bb9+eef1qFDBytdurQVLlzYGjRoYN9//32ErbHDhw93+5Bq1ar5vn/yySfu+MuWLfO99tKlS27F1A0bNlzXuQAAAAAAEJ8QrAHXYd68eS6omjJlim3fvt3GjRtnx44ds9atW7tg7YsvvrDnn3/eevTo4cI2+eijj2zNmjUueFqyZIkLx/r3729///13qH3XqlXLWrVq5UKu9evXh1pZVPtcsGCBpUuXzvr27XtdLZkKyxTkdenSxd59913buHGj27Zq1SoX5L3++uvuvEqWLGnNmzf3hYVdu3a1y5cvu/BN877dcccd9sYbb0TpuLNnz/Z913VRGOkfNn7zzTcWFBRkZcqUifK5AAAAAAAQ3xCsAdfh1VdfdVVpqlh79NFHbefOnTZ9+nR74IEH7JlnnnErb9arV8+efPJJmzx5snvPvffeawMHDrT777/frRKqSjdVbO3fvz/UvlOkSGGpUqWypEmTWubMmX3PN23a1AVTefPmdRVhOmZUJU+e3N555x27++67XcWZqukUlMn48eNdIFilShXLkyePmxMtR44cLsBTK6eOqdAtf/78dtddd9nTTz9tv/32W5SOmzFjRt93nddjjz1mq1evtgsXLrjnFTDWrFnTrVYKAAAAAECgCorrAQCB5M477/Q9Tps2rQuK9u7d60IjVZp5FJwpCBMFVF9//bULuPTaX375xT2varCoUBgX9phRpfdmyJDB93PBggV91WR79uyxQYMGuQo8j/atwC9RokQu0Pvyyy/thx9+sH379tnPP/9sV65cseioUKGCJUuWzNatW2cPPviga6kdM2ZMtPYFAAAAAEB8QbAGXIfEia8u8gwODnaVYKpEC/XLFfR/v15DhgzxtUSqDVStnJrXLKpupKor7HgVjKkizgv2evXqZeXLlw/1mjRp0rjXqS3133//dS2qGq/Cwpdfftm9RsFbeNchIroWNWrUcO2gOr6OoXnXAAAAAAAIZARrwA1SZdqWLVtcG6hn4sSJbtEChW1q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FMxdL4VjCvdUEZcnTx43fu1TYVd455o+fXq3XdV4H3/8sRUsWDDKx9L533nnne44CgwbN25sderUsdy5c7uwTfucMWPGdZ8DAAAAAADxCcEaEEVq1VQgpoCoQYMGroJMQVmSJEksVapULhTzFC5c2Pbu3esea3VPtYD6u//++0Ot+qkAKyJPPvmkHTt2zB1fFWyqHFPAdr10PAWBagP1vlRNtn///qteqwBO7aw6Zq9evezixYuWOXPmKB/L/3x0XIWI/sddvXp1uMcFAAAAACCQsHgBEEUpU6a02bNnu/nBFAypxVNVV2pzDAoK/auk9lBVt4mqzcK6fPmye40nvNd47r77btfGuWbNGvc1ePBg16KpFlHvGFGhYyokK1++fKjn06RJc9VrVRGnOeFWrFjhjq0KNLWzNmrUKNz9huV/Ptqu1k9V7PlLkSJFlMcOAAAAAEB8RMUaEEVbtmyxsWPHWrly5axnz562ZMkSu3DhggvV/v33X9ey6fnpp598E/rnzZvXfvzxx1D70s96Pio0L5uCPAVd7777rmvp/P777928btdDxzt69Khrx/S+xowZY1u3bg31Op3TgAEDLFmyZPbss8+6Vla1ci5dutRtT5o0qZvnzXPo0KFIj6tr43/cTz/91L766qvrGj8AAAAAAPENwRoQRaqw0mqXqlpTULRo0SI7d+6cnTx50m3XogC//vqrC6AURj399NPu+ZYtW7pWSAVk+/bts/fff9+1YGp1zIiotXT37t12+vRp96UFBDZs2OBCLC10kDVrVsuQIcN1fXYKySZPnuzGcfDgQdcWqkUYwraVqtpMiw+oQk3trAoJtfqpN8eaVkTVIgo6V60IqpbYa9H5f/nll27VVB130qRJ7kvzrwEAAAAAEMhoBQWiSKtkKuAaNWqUW/lTixgonMqUKZPbrgn5n3rqKReKdenSxc3FJrVq1bK///7bhg0b5uZK034URl1rnjQtdqAVSBVE9ejRw1Wavfrqq24FT83fpvnPNLfb9fAfh77fddddbj/hBVxDhgxx56jwTxV5NWvWtJdeeslt06IHqthr2LChm2OuY8eO1rlz5wiPq/nkdC5a5VTftajBBx98YKVLl76u8QMAAAAAEN8kCtGShgCiTVVbWuly165dXMVY1Kgfq4gCuD6j2ta+6ZcsKCixZciQ2k6cOGvBwf+bSxPg3kJ8xL9Z4L5CoAiKo//Hypw5baSvoWINQECY3acpf6giRvHHBAAAAIAbRbAGBCi1pWqus4i0bt3a2rRpc1PHBAAAAADArYRgDbhBZcuWjZM20LZt29ozzzwT4fZ06dLd1PEAAAAAAHCrIVgDAlTGjBnd162COdaAhCEu5j0DAAAAYkviWNszcIs7fPiwFShQwH0HAAAAAAAJD8EaAAAAAAAAEA0EawAAAAAAAEA0EKwBsWzFihVWvXp1K1asmFul89SpU+75LVu2WNOmTe3++++3qlWr2owZM3zv6dGjh/vyp7bSjRs3uscbNmywevXqWZEiRaxatWo2c+ZM3+v+/fdfe/XVV61EiRJWsWJF69+/v/3333925coVK1OmjK1evdr32kceecS6d+/u+3nw4MHWtWtX93jlypVWv359d4xSpUpZly5d7OzZs27b8OHD7aWXXrKnn37a7XPTpk128eJFGzBggFvMQV/az8mTJ337njJlilWpUsXtr2HDhrZ58+ZYuNoAAAAAANw8BGtALJs3b54LrBQsbd++3caNG2d79uyxFi1aWOnSpW3u3LnWvn17e/fdd2358uWR7u/y5cvWqVMnq1mzpi1evNg6duxob775pv32229ue+/eve306dMuqBs1apT99NNP1q9fP0ucOLGVL1/ehWDy559/2sGDB+2HH37w7fvrr7+2SpUquee136eeesodY+jQofbNN9/YrFmzfK9V8Fa7dm2bPHmyFS1a1J3jzz//7M5P53rmzBm3D/nll1/svffes759+7r9KajTOSjsAwAAAAAgULEqKBDLVD2m4EkeffRR27lzpwuoChYs6KrAJF++fC5sGz9+vD388MPX3J9CM1WCZcqUyXLmzOm+smTJYpkzZ3aBmCrkFJ6lTZvWvV4Va6o869mzp6tg8yrjVDFWoUIF+/bbb+3vv/+2pEmTurEpWFPV22uvvWaNGzd2r9UxHnjgAdu9e7dvHDq+Ku7k/PnzNm3aNPvss89cZZ0oSFPl2q5du+zIkSOWKFEiy549u9uXQjVVrylYU+AHAAAAAEAgIlgDYtmdd97pe6yw68KFCy5E88I2T/HixUO1dEYkffr0LtBS8KWKNAVUjz/+uKVLl85Vnymsqly5cqj36LkDBw64YE1VYwrnvvvuOxesnThxwr7//nv3OoViGTNmdF/JkiWz0aNH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jhyxdoz06dPH2r4Rt5IkSWKZM2fmYwAAAAAA3NJoBb0FqW3yyJEj1qtXL/f4+++/t6ZNm7q20Pvvv99eeOEF++uvv9xrL126ZK+99pqVLVvWihcvbm3atLE///zTty9tf/PNN61EiRL2wAMP2McffxxhK6haNh999FErWrSoNWzY0L777rtQY5o+fbo1btzYihQpYvXq1bOff/75us5r8ODBbhyVKlWyqVOn+p6/ePGivf322+75QoUKuWN9+umnvu3//fef9e7d2wWNes3s2bOtYMGCvjbHKVOmWJUqVdy4NO7NmzdHaTwhISE2ZswYd7zChQu7CsERI0b4tgcHB7sx63kdu0OHDnbixAm37dy5c9anTx933fX1+uuv24ULF9y2f//911599VV3rnpv//793Tn4Xwc9r+usz2D37t1R+ixXr15tDRo0cO+rVauWLVu2zLdN+9FxqlWrZg899JDt2rUrVCtodMcEAAAAAEAgI1i7Bc2ZM8eyZs3qgjUFUK1bt7YKFSrYwoULbcKECXbw4EH76KOP3GsVdikAmzhxonvf2bNn7a233vLta8uWLa7dc/78+fbiiy/aO++8Y3v27LnqmArVFLboWHqtQji93j/YUQin5xYsWGBp06a1AQMGRPmcFBQq7FFg1qVLF3v33Xdt48aNbpvOZc2aNW7/S5Yssfr167ux/P333267jqPz0LkPGTLExo8fb5cvX3bbfvnlF3vvvfesb9++tnjxYitVqpR16tTJrly5EumYdJ6TJ0+2gQMHuuOq7VZj2L59u9v+4Ycf2rx589z11LiPHz/ujiMKwBR4jho1yl17PR46dKjbphBQFYczZsxw23/66Sfr16+f27Z8+XK3L71Wn2emTJmsZ8+ekX6WGzZssPbt27tA8/PPP7dGjRpZ586dQ4Wb+gwHDRrkwsHUqVOHOtfojgkAAAAAgEBGK+gtSPNiqZVP4VWyZMnspZdesmeffdYSJUpkuXLlskceecS2bdvmXquKpOTJk7uWUbV2Kjg7efKkb1933HGHC0n03pYtW9rIkSNdwJU/f/5Qx1SAp0olhVrStWtXF/JMmzbNXnnlFfecqqWqV6/uHms8HTt2jPI5aYwaW4YMGezuu++2TZs22cyZM1111r333mvlypVz1XiiSi2Nc//+/ZYyZUoXgI0bN863XaHW888/7wvsdG7Zs2e3nDlzulBN1WsK1hInThzpPGSqlCtfvrz7WVWBOq6qtVQRN2vWLOvevbtbREJU+afw7tSpUy6IU/WfKtlEIdWOHTtc6LlixQp3fvr8RCGhrqs+B41XQafGqy9Vuu3duzfSz1KhW40aNdxnKHnz5nX3gEI4VZuJKtVUkebty3MjYwIAAAAAIJARrN3iNE+WApBJkya54Oa3335zwZgXoDz55JO2aNEi18ZXpkwZF3ypHdKjsEnBk0fBitey6E9VbKrY8qcgy7+6LU+ePL7HadKkca2LUaVAUKGaR8GVWjpFY/76669dkKRAR1Vooqo0/azjqM3TozZJj877nnvusTp16rh9qhVS1VxBQZH/6ijM+/HHH+2DDz5w56nre+zYMRfKqeVToZZaUz133XWXqxpToKWx+W9TpZy+1K6p93thnEfPHThwwB577DEXVmqcur469yeeeCLSz1Lja9KkSah96jp89tlnvp8jmo9P743umAAAAAAACGQEa7c4tWI+/vjjLsRRe6bmOFPbpAIhUfXXqlWr3HP6UvWS2vlU4SSqfAtvbrGwVCkVlsIj/5bKG1lBNGz1mPbr7U/tnQrZFCIpRFS7peY9k/ACMv/xq6JN71U1lkIttUOq3VHfVa13LXqfWi0VxKkKUNVpzZs3j/C4UbkOumYKL/0DL4/GkyJFClf1piBR41V7qyrjVJV3rc8yvM9H19D/8wnvNTc6Jl1fAAAAAAACFXOs3eI0/1W6dOls7Nix1qJFC1cVdejQIV+4pPBDYYgWHdC8ZZp/TPN9aT6w66HWQi+s8+hnPR8TNObz58/7flbVV758+dxjtYSq/VDtp5qU33udzvHOO+90QZb/XGL+jzX3mq6Nqs/U1qgWTVXk6RpERgGcqvQ0l50CPVXU6brpuLfddpv7eefOnb7Xq6JNVV+qAlRg6b9NrZZqldX10lxmqhLMnTu3+9IiAZoHTos0KDBToKe2TbWWar40tbz++uuv1/wsw/t8dO5R+XxuZEwAAAAAAAQyKtZucZpr6/fff3eT1yvQUWWRVoP0WiMVmGhlS4VA2v7FF1+4hQ/82y6jQnN3aYJ7zb2m1UdV3aTgSO2ZMUFhlyrC1EqpsGjp0qUuUPPOUYGSVuZUhZ43Yb9CH03Cr0o2LTCgRQwUeumxKChStZXmRdOE+5orTfPCacVOrYgZGV0jXVe1QGqhAFXOqe1UxxXNOacFDFTVdfvtt7vjqlVS1V8K4vSzgiiNQ+9V6Kbrp5VLFRJqLjgFcAoNFY4qrFOFmQIttfjed999rvVTVWFqs1XYGNFnqc/nqaeecostPPjggy4MU+iq6rLI3MiYAAAAAAAIZARrtzhVLyks6tChgwtwFKgpoNLqlQqAnn76aTt69Ki9+uqrblJ9hVOjR48OtwX0WlQpplU4hw0b5uYZU8CiifHDLnIQXdqfAiq1siooUnimsYoev/HGG26uL71GrZkav1chpvNVe6jCJc3tpnNWkKVKNu1XAZdWutQCApp8XytjRmXcqlTTl1baVHCma61ASccVrYCq4FILIgQHB7uKLgVS3nt1XC3ioHHo+mmVTlFIpRBQ41VLqUItBVqiFld9llo0QddZVXsau0Kua32WCju1X33uOj9VoWkVT2/hhchEd0wAAAAAAASyRCHhTYgF3ELUZqkASdVrosouVW+pFfJG5n1DzGrUbwaXFIgBo9rW5jrGoqCgxJYhQ2o7ceKsBQf/b55KgHsL8RH/ZoH7CoEiKI7+Hytz5rSRvoaKNdzyRowY4VpFVUGmlk1VbKnKilAtfpndpyl/qCJG8ccEAAAAgBtFsIZ4TdVjWlQhImrN1JxdN+L999+3/v37u3nNkiVL5kI1tWJei+Zw69GjR4TbS5Ys6RYHAAAAAAAACRetoIjXNM/bH3/8EeF2zeeVI0cOu9lU2aY54yKiRQ80nxtiFq1ViElUrCE2cF8htnBvgfsKgYJ/rxAbaAUFokkVZLlz545310/zsXlzsuHmYI413OqYGw0AAACIfxLH9QAA3DzNmjVzK3/eqEOHDtnatWuj/HodU+2xpUqVsjNnzthLL71kRYsWdeMBAAAAACBQMccagOumOejKlCljDz74YKSvPXXqlFsgQvPYVahQwb799ltbt26dzZgxw7JkycLVBwAAAAAELCrWAMQqVahJ+fLl3Xx4p0+ftkyZMlnhwoUJ1gAAAAAAAY1gDYinDhw4YM8995wVL17cHnroIZsyZYp7fs+ePe75EiVKWKVKlVw12JUrV3zvW716tTVo0MC1WtaqVcuWLVsWreNv2LDB6tWrZ0WKFLFq1arZzJkz3fNaDXXTpk3uuGrlPHz4sBUoUMB992/99LZplVWpXr26e6z3//777+49c+fOvcGrBAAAAABA3KEVFIiHLly4YK1atbJChQrZrFmz3Jxmr7zyiqVLl87eeustF1DNnj3b9u3bZ6+99pqlSZPGWrZs6cKw9u3bW9euXV2b5po1a6xz58726aefugqxqLp8+bJ16tTJ7bNOnTr2ww8/WPfu3d0cab1797b9+/e7wK9169a+irTwZMuWzY2zUaNG7nvevHldmDZx4kSbM2eOpU2bNoauGAAAAAAANx/BGhAPrV+/3v755x8Xoik0u/vuu12AdvLkSUuZMqWbrywoKMjy589vx44ds5EjR7oQbPr06VajRg33WBRkbdu2zQVZgwcPjvLx1a6pY6llM2fOnO5L86FlzpzZhWFJkya1VKlSWfr06a8ZrCVJksQyZszoHuu73qsvPa99AQAAAAAQyGgFBeIhVaIpFFOo5nn88cdt7969ropNoZpHlWMK1/7991/XJqoWUH/aruevhwKzpk2bujCvSpUq1q9fPxeIqWIOAAAAAAD8H4I1IB7yD878JU+e/KrnvPnV1L4Z0Xb/Odii6o033rCFCxda48aN7ccff3Tf165de9XrEiVKdNVzwcHB1308AAAAAAACDcEaEA/lyZPHLV5w/vx533PvvvuuffLJJ7Z9+3a7dOmS7/ktW7a4NktVmanKTSGYP23X89dDFXBvvvmm5c6d29q2bWufffaZlStXzlatWnXVa9UWKmfPnvU957+QAQAAAAAACRXBGhAPVaxY0c1v1qdPH9fGuXLlSrcq59ChQ+3ixYu+51esWOFW4FTbpirHNLfa0qVLbfLkyW6BgUmTJtny5cvd9uuhlk+9T3O8HTx40L777jvbuXOnFSxY0G3X/Gra//Hjx904tUjBhAkT3CILWpxAiyYAAAAAAJDQEawB8bQVdNSoUfbXX39ZgwYNbODAgdatWzerXr26jR8/3oVd9evXd4sYtGjRwl5++WX3vmLFitl7771nM2bMsNq1a7tKM4Vx5cuXv67jJ0uWzB1fYVrdunXdCqFPPPGEW91T9H3dunX2/PPPW+LEid34tEhCrVq1bMmSJdamTZtYuS4AAAAAAMQniUJCQkLiehAAEJlG/WZwkXBLG9W2dlwPAVEQFJTYMmRIbSdOnLXg4Ouf3xLg3sLNxL9Z4L5CoAiKo//Hypw5baSvCX+GdACIZ2b3acofqohR/DEBAAAA4EYRrAG3oHbt2tk333wT4XYtXKAWUAAAAAAAEDGCNeAW1Ldv31ArjoZ1++2339TxAAAAAAAQiAjWgFtQlixZLNAwxxpuFcylBgAAAAQOVgUFcE07duywH374gasEAAAAAEAYBGsAIp2Pbf/+/VwlAAAAAADCIFgDAAAAAAAAooFgDUCEmjVrZkeOHLGePXtajx49bM+ePfbcc89ZiRIlrFKlSjZixAi7cuWK/ffff+65ZcuW+d576dIlK1u2rG3YsMH+/fdfa9++vZUqVcpKly5tXbt2tTNnznDlAQAAAAABjWANQISGDx9uWbNmtV69erlg7KmnnnILH8yePdutLDpt2jSbMmWKpUiRwqpXr25Lly71vfebb76xoKAgK1OmjA0bNsyOHTtmM2bMcK/fuXOnjRo1iisPAAAAAAhorAoKIELp06e3JEmSWNq0aW3lypWWMmVK69+/vwvM8ufP78KykSNHWsuWLe2xxx6zzp0724ULFyx58uS2ZMkSq1mzpnu/qt5Sp05tOXPmdPv48MMPueoAAAAAgIBHxRqAKFEbaKFChVyo5ilevLgL19TqWaFCBUuWLJmtW7fOtYGuWLHCatWq5V7XvHlzt7Jo+fLlrW3btvbTTz9Znjx5uPIAAAAAgIBGsAYgSlSFFpbmV5PLly+7wK1GjRquHVRtoGnSpHHzrokCtbVr17r2UYVvffr0se7du3PlAQAAAAABjVZQAFGSN29etziBqtGSJk3qntuyZYtlzJjRtYxKnTp1rF27dpYqVSrXBpooUSL3/KRJk6xAgQLWoEED97Vo0SK3IAIAAAAAAIGMijUA16SQbO/evVa5cmW7ePGiqzZTW6haPbW4QdOmTX0BWsmSJd0cavPmzXNzrnmOHj1q/fr1s61bt9r+/ftdVVvBggW58gAAAACAgEbFGoBrUnD2/vvvu0Bs/PjxNnDgQKtfv76rVGvRooW1bt3a91oFbKpUW7VqlRUuXNj3fMeOHe306dNufrVz585Z6dKlbdCgQVx5AAAAAEBAI1gDcE1PP/20+/JMnz79mq/XYga1a9cO9Zyq2BTIAQAAAACQkBCsAYgRavPcvn27rVy50hYuXBjjV3V2n6Z24sRZCw7+vwUTgBsVFJTYMmRIzX0FAAAAINoI1gDEiHXr1tnEiROtc+fOljNnTq4qAAAAACDBI1gDECPat2/vvgAAAAAAuFWwKigAAAAAAAAQDVSsAQgIjfrNiOshAD6j2oZeoAMAAADArYmKNQA+hw8ftgIFCrjv16tHjx7uCwAAAACAWwXBGgAAAAAAABANBGsAAAAAAABANBCsAbjKkiVLrHLlylaiRAnr06ePXbx40T0/e/Zsq1mzphUuXNjKli1rb775pl2+fNn3vjNnzthLL71kRYoUsTp16ti3337rnl+wYIF7fXBwsO+1S5cutYceeshCQkL4BAAAAAAAAYlgDcBVZs2aZUOGDLExY8bYV199ZWPHjrVNmzbZgAEDrEuXLi54U6g2Z84cW7lype99y5cvt3vuucfmz59vFSpUsJdfftlOnz5t1apVs//++88XtMnixYvt0UcftUSJEvEJAAAAAAACEsEagKv06tXLSpYsaWXKlLGOHTvazJkzLVWqVDZw4EB75JFHLGfOnK5yrWDBgrZ7927f+1TJ1qlTJ8ufP79169bN0qdPbwsXLrTUqVNblSpVXCAn58+ft7Vr19pjjz3G1QcAAAAABCyCNQBXKVq0qO+xwrO///7bcuXKZffee68NGzbMOnToYDVq1LAff/zRrly5Eu77EidObPfdd5/t2bPH/Vy7dm1bsWKFawdds2aNZcmSxQVxAAAAAAAEKoI1AFf/w5D4f/80eHOgfffdd9awYUMXslWqVMkFbJqDzV+SJElC/azQLWnSpO6x5mzTfGzaj+ZXUxsoAAAAAACBjGANwFV+/fVX3+Nt27ZZ1qxZ3QIEjz/+uPXr188aNWrk2j0PHjwYavGBXbt2+R6rMu2XX36xfPnyuZ+TJUtmDz/8sJuH7euvv6YNFAAAAAAQ8AjWAFylf//+rs1TAZgq01q2bOnmS9uyZYsLzzSvWo8ePezYsWO+FUNl8+bNNnr0aNf+qYUOLl265FpAPXqsBQ8U1N19991ceQAAAABAQAuK6wEAiH+aNm1qbdu2dcFY48aNrUWLFq4FtGfPnvbkk09amjRp7MEHH3Sv27Fjh+999evXd+HayJEj3eqgWk00ZcqUvu1ly5Z1CxnUqlUrjs4MAAAAAICYQ7AGwEerfXrtnE899VSoK6PFBiZMmBDh1XrnnXcivZJaDfTcuXOhqtgAAAAAAAhUBGsAYp3mYdOCBcuWLbPixYu7FUav1+w+Te3EibMWHPy/VUiBGxEUlNgyZEjNfQUAAAAg2gjWAMS6RIkS2aBBg9yqoZqDDQAAAACAhIBgDcBNsXLlSq40AAAAACBBIVgDEBAa9ZsR10PALWhUW+YDBAAAABCxxNfYBiAemDt3rlWtWvWmHOvQoUO2du3aGNlXjx493BcAAAAAAAkVwRoAn169etm2bdu4IgAAAAAARAHBGgAAAAAAABANBGtADLVQtmzZ0ooVK2Z16tSxCRMm+No3Z8+ebTVr1rTChQtb2bJl7c0337TLly+HapesW7eulS9f3vbv329//vmnPf/883b//fdbgwYN7ODBg6GO9euvv1qzZs2saNGiVqNGDZs+fbpv2/Dhw+2VV16xvn37WokSJdw+x40bF6Vz0Dg2bdpkI0aMcPuXo0ePWseOHa1MmTJu7AMGDLCLFy/63rNlyxZr2rSpG6vOd8aM8OdB+/fff619+/ZWqlQpK126tHXt2tXOnDkTjSsNAAAAAED8QbAG3KDg4GBr3bq13XbbbfbZZ5/Ziy++6MIpUVClMKpLly62ZMkSF6rNmTMn1AqZn3/+uXXq1MnGjh1refLkcUHWlStXXCD3wgsv2OTJk32v/e+//9xzJUuWtAULFlj37t1t1KhRNn/+fN9rli5dasmTJ7d58+bZc889Z++//77t27cv0vPo3bu3FS9e3Fq1auUCOgVoLVq0sPPnz9vUqVNt6NChtmbNGnvvvffc6/fs2eO2KyjTPHAKzt59911bvnz5VfseNmyYHTt2zAVvU6ZMsZ07d7pxAwAAAAAQyFgVFLhB3377rf3xxx82a9YsS5Mmjd11112uqmzRokWWKlUqGzhwoD3yyCPutTlz5rSPP/7Ydu/e7XuuSJEivuo2Pa8qsNWrV1v27Nnt7rvvtp9//tmFcvLFF1/Y7bff7oI4URB35MgRF1bVr1/fPZc+fXoXuCVJksRVvqliTfvImzfvNc8jbdq0ljRpUjdm7UPhn6rndF7p0qVzr+nTp4+1bdvWOnfu7J4vWLCgCw0lX758LmwbP368Pfzww6H2rTGmTp3anX/KlCntww8/5L4DAAAAAAQ8gjXgBu3atcuFVgrVPGqNVLCm9s8UKVK4iq3ffvvNvfbAgQNWsWJF32tz5Mjhe6zXKNRSqOZR8OYFa3v37nXVXqos86itVCGaR+GV/88KtFRVd70Ukim480I1UXup9qX2VG1XO6o/jWvmzJlX7at58+b20ksvudZUfamFVS2zAAAAAAAEMoI14AYpxAoJCQn1nPfzunXrrF27dq6arFKlSu6x2kH9qW0zvPd6VEXmUailYEqVYxHxf31E+4yKsOMSb244fQ9vu1pYvdf405jXrl3rquDUTqrxr1+/3rWpAgAAAAAQqJhjDbhBatfUogP+k/Fv377dfdc8aY8//rj169fPGjVqZPnz53fVXhEFXffcc4+dOnXKVbV5duzY4XusyjjNl6aqtNy5c7uvrVu3ujnQYpqOpfM6efKk7zkdKygoyO688063/ccffwz1HrWxhtdyOmnSJHdNtBiD2kDffvttW7ZsWYyPGQAAAACAm4lgDbhBqsbKli2bvf766649Um2bmvNM1NapsEktoJo/TStvahJ//5U1/Sl40/569erlWj5XrFhh06ZN823X6qFawEAVXzqWqsA0h5vmXYsJml9NYdrx48etQoUKlitXLuvWrZsbv+aS69+/v9WuXdst1PDUU0+50G/w4MEu7NNiCZ988ok9/fTTV+1Xq4sqXFQwp/1rgQXNzwYAAAAAQCAjWANu9JcocWK3iqYm+q9Xr55b7bJhw4auJfPll192odeTTz5pzz77rGufbNq0aagqtLCGDBliGTJksCZNmrjQqlmzZr5tmsdNixEonFJ76WuvveaCLK1KGhNUVaf2VS16oBZXb+XOxo0bu0UKqlWr5gIy0TxwWslUr9d8aaNHj3bBoSr0wtJKp5qfTQsf6BqdO3fOBg0aFCNjBgAAAAAgriQKic7kSwB8VN31yy+/uDnUPFoZU9VksdGieatq1G9GXA8Bt6BRbWvH9RAQYIKCEluGDKntxImzFhx8Ja6HgwSEewvcVwgU/HuFhHRfZc6cNtLXsHgBEANUiaX2zQcffNDNjzZ58mRr06YN1zYGze7TlD9UEaP4nz4AAAAAN4pgDbhBavUcOnSob1L+TJky2TPPPOPmIItP1J6qudAiohbTUqVK3dQxAQAAAAAQyAjWgBhQvXp19xWfjRgxwi5duhTh9jvuuOOmjgcAAAAAgEBHsAbcIrTYQCBjjjXEFOZNAwAAABBTWBUUSMDOnDlj8+fPv+H9bNy40QoUKBAjYwIAAAAAIKEgWAMSsEmTJtlnn30W18MAAAAAACBBIlgDErCQkJC4HgIAAAAAAAkWwRoQzx0+fNi1YX7xxRdWqVIlt3LngAEDLDg42G1fvny51apVy4oVK2ZPPPGEbdq0yT0/d+5ct2CBfo5qG+eUKVOsSpUqVqRIEbeK6ObNm0NtnzFjhhtD8eLFrWfPnnbx4kXfttWrV1uDBg2saNGibjzLli3zbWvWrJkbS9OmTd04tWLqnj17YugKAQAAAAAQNwjWgAChYGrIkCHuu0Kr4cOH286dO6179+7Wtm1bW7BggdWtW9deeOEFO3DggAu3WrVq5UKw9evXR7r/X375xd577z3r27evLV682AV4nTp1sitXrvhes3TpUpswYYIbw5IlS3xtphs2bLD27dtbvXr17PPPP7dGjRpZ586d7eeff/a9d+zYsVajRg0X+GkF0hdffDFUMAcAAAAAQKBhVVAgQLz66qsu7JKOHTva+++/b7///rs1btzY6tSp455v3ry5fffdd66yrEePHpYqVSpLmjSpZc6cOdL9HzlyxBIlSuRWD82ZM6cL1VS95h+sKXTLmzev3XPPPfbAAw+4YE+mT5/uQrOWLVu6n/Wabdu22cSJE23w4MHuucqVK/u29+/f31W+ff311+4YAAAAAAAEIoI1IECUKFHC97hw4cL2zz//2JYtW+zo0aP26aef+rZdunTJKlaseN3713sUmCmkK1iwoFWrVs1VngUF/e+fiTvvvNP3OG3atL6KM7V1NmnSJNT+VCnnv3CC//jTpEnjwje9j2ANAAAAABCoCNaAAKHKM49XRZYyZUrX+lm/fv1Qr02RIsV171/7mj17tpuTTfOlqWVTlW/67kmSJEm4iyMkT578qv1pjP7Vbv4BnVy+fNkSJ6YbHQAAAAAQuPirFggQO3bs8D3W3GVZsmSx/Pnzu8UNcufO7ftS9dpXX33lXqfWzqhS9ZvmQStXrpxbmEBzqF24cMG+//77SN+r6rMff/zxqv3peY/XNiqnT5+2gwcPRnlRBQAAAAAA4iOCNSBADBw40H766Sf75ptv7MMPP7Snn37azVn25ZdfutU8FVRNmjTJfeXJk8dXhfbXX3+58C0yqnIbOXKkq1rT6xctWmTnzp2LUvilcWhhg8mTJ9v+/fvdGLRaqVYB9WhV0/nz57v2z969e7u53MqWLXuDVwUAAAAAgLhDsAYECK3y2bp1a+vSpYub+0yrat5///1uJc9PPvnEbZ81a5Z98MEHVrp0afeehx9+2LVjPvbYY3b8+PFr7v++++5z4d348ePt0UcftTFjxtigQYNcVVxkihUr5sah1tHatWu7udWGDh1q5cuX971Gc7fNnDnTGjZsaGfPnrVx48Zd1R4KAAAAAEAgSRTiTZIEIF5S9ZgWEli5cqVbrTMQNWvWzMqUKWPt27eP9j4a9ZsRo2PCrWtU29rue1BQYsuQIbWdOHHWgoP/Nx8gcCO4rxBbuLfAfYVAwb9XSEj3VebMaSN9DeUiAALC7D5NCUAAAAAAAPEKwRpwi9B8ZhcvXoxwu+ZU07xnAAAAAAAgagjWgHhO7Z+7du264f3MmTPHzbcWEa0yGlumTp0aa/sGAAAAACCuEKwBt4hcuXJZIGOONYQ3TxoAAAAAxCVWBQUSKC12ULlyZbdi57p16+J6OAAAAAAAJDhUrAEJ1LBhw6xixYrWrl07u/322+N6OAAAAAAAJDgEa0ACdfr0aStZsqTlyJEjrocCAAAAAECCRCsoEE8cPnzYChQoYF988YVVqlTJSpUqZQMGDLDg4GC3ffny5VarVi3X2vnEE0/Ypk2bfO9t1qyZ9e/f36pVq2YPPfSQWwH0yJEj1qtXL6tatapv3/ruGT58uHufzJ071z0ePXq0lS5d2ipUqGDz58+3JUuWWJUqVdxYBg0a5HuvVhfV2HQcfXXt2tVOnjwZ6jxGjhzp9qUxlChRwpYtW+Z7/6VLl9z7NmzYcFOuLQAAAAAAsYGKNSCeGTFihA0ZMsQFat26dbPUqVPbo48+at27d7c333zTihYtamvXrrUXXnjBFixYYLlz5/aFYxMmTLBkyZJZ9uzZrUGDBtaqVSurU6eOnTt3LtLjbtmyxS1woNVDp0+fbm+88YYVLFjQhW0///yz9e7d2x577DH33ODBg91z48aNs+TJk7vxduzY0SZPnuzb3w8//GCfffaZW4lU57J06VJ75JFH3LZvvvnGgoKCrEyZMrF4JQEAAAAAiF1UrAHxzKuvvuoqxMqVK+fCqlmzZrnArHHjxi4kU5DWvHlztzDBjBkzfO9TpZoqwwoXLmwZM2a0JEmSWNq0ad3jqAgJCbHXXnvN7f/JJ5+08+fPW/v27e3ee+91FXKap23v3r3u+WnTpvlCPlWnvffee66CbteuXb79tWjRwu68807LkyePC+RWr15tFy5ccNtUCVezZk03RgAAAAAAAhUVa0A8o3DMo5Dsn3/+cdVkR48etU8//TRUO6UWJ/Dc6FxqCs5SpUrlHqsKTXLmzOnbniJFCtcCeujQIXfsJk2ahHq/KtP2799vhQoVumo8ai1VJZ1WJ33wwQdtxYoVNmbMmBsaLwAAAAAAcY1gDYhnkiZNGiqskpQpU7rWz/r164d6rcIujxeGhSdRokRXPefN3eZRa2ZU3nf58mX3/ZNPPvEFcf7hnDfXmv94tO8aNWq4dlCdX5o0aUIFiAAAAAAABCJaQYF4ZseOHb7HmscsS5Yslj9/frcogNo0vS9Vr3311VfXFdadPXvW95z/QgbXQ/OwqYVTAZo3FgVlb7/9th0/fjzC96mNVeNdtWqVawMNL7QDAAAAACCQEKwB8czAgQPtp59+chP8f/jhh/b0009by5Yt7csvv7QpU6bYwYMHbdKkSe5L85dFRaZMmSxbtmxurja1cmqhgzVr1kRrfArRGjVq5BY32Lhxo/32229ukYUDBw6Eah0Nq2TJkq7ybt68eW7ONQAAAAAAAh3BGhDP1KpVy1q3bm1dunRxAdaLL75o999/v1sgQO2X2q4FDT744AMrXbp0lPaZOHFiF9ht27bNvV+LB7Rp0ybaY+zRo4eVL1/eOnTo4BZVUKvnRx99dM3FCFShpkq1rFmzurnjAAAAAAAIdIlCtBQggDin1sxq1arZypUrr1n5FcheeeUV1zqqQO56Ner3vxVQgVFta9/wRQgKSmwZMqS2EyfOWnDw/81nCHBfIb7i3yxwXyFQ8O8VEtJ9lTlz2khfw+IFAGLd1q1bbfv27S40XLhwYbT2MbtPUwIQAAAAAEC8QrAGINatW7fOJk6caJ07d06w1XgAAAAAgFsPraAAAgYte4hJtCkgNnBfIbZwb4H7CoGCf69wq7WCsngBAAAAAAAAEA20ggIICCxekPDExAIEAAAAABCXqFgD4qG5c+da1apVb3g/Fy9etFmzZlls6dGjh/sCAAAAAOBWRMUakIAtWrTIxowZY40bN46V/ffu3TtW9gsAAAAAQCAgWAMSsJCQkFjdf9q0kU/kCAAAAABAQkUrKBCH/vjjD2vTpo0VK1bMtX6OGDHCLl++fNXrfv31V2vWrJkVLVrUatSoYdOnTw+1/fPPP7eaNWu6/TRp0sR++eUX27hxo/Xs2dOOHDliBQoUsMOHD7t99O/f36pVq2YPPfSQnTlzxo4ePWodO3a0MmXKWNmyZW3AgAGuhdRrSdV7hg0b5raVKlXK3n77bV9gF7YVNLxxyO+//26tWrWy4sWLW/ny5d0YLl26FMtXFwAAAACA2EWwBsQRhVMvv/yy3X777TZv3jwXWH3xxReuddPff//9Zy+88IKVLFnSFixYYN27d7dRo0bZ/Pnz3fZ169a5lswWLVq47YULF7bWrVu7EKtXr16WNWtWW79+vWXLls0Xlg0aNMiFeMmSJXPvO3/+vE2dOtWGDh1qa9assffee893/C1btti+fftsxowZ9vrrr9uUKVPsm2++uep8IhqHQjoFaalSpXJjHjlypC1dujRW534DAAAAAOBmoBUUiCPffvutq+SaPXu2JU6c2PLly+dCM1WZ6btHYZvCt06dOrmf8+TJ46rQFHDVr1/fPv30U6tdu7Y1bdrUbe/WrZslTZrUTp065Vo1kyRJYpkzZ/btT5VqJUqUcI9Xrlxpf/75pwu50qVL557r06ePtW3b1jp37ux+VgWdgrE0adK4MU6aNMl++uknq1ChQqjzudY4NN5ChQpZ9uzZLXfu3PbRRx/ZbbfdFuvXGAAAAACA2ESwBsSRPXv22MmTJ10lmufKlSuuQk3Pe/bu3Ws7d+50FWgehV0KzETVZGq79KgKzT+YCytHjhyhxqCgzgvVRKFbcHCwHTx40P2sUE+hmkePtT2sa43j+eefd9Vzy5cvt8qVK1utWrWsYMGCUb5WAAAAAADERwRrQBxROKUKMLV1hrVp06ZQr9O8ZKokC09Q0PX9GidPnjzcxx5vjjfvuwKyqCyKcK1x1K1b153DihUrXKtphw4dXHurVxUHAAAAAEAgYo41II7kzZvXtYJmzJjRtUfqSwsMaKGAsK9TNVjOnDl9r9u6daubE030syraPArEtBDC999/b4kSJYp0DPv37w9VIad9KyS78847r+t8rjWOIUOG2PHjx12b6NixY11b67Jly65r/wAAAAAAxDcEa0AcqVixomvLfPXVV23Xrl22efNmtzhAypQpfW2eXrWX2kNVsabWzbVr19rAgQNdi6Zo1U4tFqAFEA4cOOBbtVNzmmlfmuNM4Vl47ZuaJy1XrlxuPjSNQfO+aT41zZV2vXOgXWscamft16+fC952797tzoFWUAAAAABAoCNYA+KIwrPRo0e7edUaN25s7du3twcffNBee+21UK/TnGbjxo1z4ZgWK9D2p59+2q24KaVLl7a+ffu61TYVwu3YscOtLJoiRQorV66cqySrU6eOez68MXitqBpDly5drFq1ai4Eu17XGscbb7xhmTJlcuGbjpMlSxa3gigAAAAAAIEsUUh4kyUBQDzTqN+MuB4CYtiotrXj9JoGBSW2DBlS24kTZy04+EqcjgUJB/cVuLcQSPg3C9xXCBRBcfT/7pkzp430NSxeACAgzO7TlAAEAAAAABCv0AoKAAAAAAAARAPBGgAAAAAAABANtIICCAjMsRb44npONQAAAACIaVSsATfZ4cOHrUCBAu47AAAAAAAIXARrAAAAAAAAQDQQrAEAAAAAAADRQLCGW8KBAwfsueees+LFi9tDDz1kU6ZMcc/v2bPHPV+iRAmrVKmSjRgxwq5cueK2DR8+3F555RXr27ev216+fHkbN26cb587d+60Jk2aWLFixXzv9Vy4cMEGDRpkDz74oN1///3Wpk0b++OPP8Id27///muvvvqqO0bFihWtf//+9t9///m2Dx482D1ftGhRa9asme3evTvK5z1p0iQ3Nu17wIAB7v1z58512/7880/r0KGDlS5d2goXLmwNGjSw77//PlS76po1a6xq1aruuun9v/76qzVs2NCdU+vWre3MmTO+Y82cOdP3Wh1n165dvm0bNmywevXqWZEiRaxatWrutQAAAAAABDqCNSR4CrlatWplqVOntlmzZlmfPn1syJAh9vnnn9tTTz1lWbJksdmzZ7sAbdq0ab7QTZYuXWrJkye3efPmuQDu/ffft3379rlt3bp1s/vuu88WLlxoAwcOtPHjx9vatWvdNu1r+fLl9u6777oQKTg42F566SVfaOevd+/edvr0aZsxY4aNGjXKfvrpJ+vXr5/bpn18+umnNnToUHecTJkyWc+ePaN03gsWLLBhw4ZZr1693D4Uln333Xe+7V27drXLly+78c2fP9/uuOMOe+ONN0Lt46OPPnJjUtg3depUe/nll13YOGHCBNu6davNmTPHvW7VqlUuWHz99dfdtSpZsqQ1b97cTp065Y7RqVMnq1mzpi1evNg6duxob775pv3222/R+jwBAAAAAIgvWBUUCd769evtn3/+sbfeesvSpEljd999t7322mt28uRJS5kypQuNgoKCLH/+/Hbs2DEbOXKktWzZ0r03ffr01r17d0uSJIk9//zzrmLt559/trx589qRI0dc9VWO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7QgAAAAASBgI1gDEuqlTp3KVAQAAAAAJDsEagIDAHGvX71aZKw0AAAAA4go9WQAAAAAAAEA0EKzdYo4fP26LFy+OlX2fOXPG5s+f7/u5atWqNnfuXIttWth2+vTpMbKvw4cPW4ECBdz3QLRjxw774YcfYmXfhw4dsrVr1yaI6wQAAAAAQEwgWLvFvP/++75wJKZNmjTJPvvsM9/Pc+bMsVq1alls++6776xfv36xfpxA0K5dO9u/f3+s7LtXr162bds29zhbtmxulU99BwAAAADgVsUca7cYVXfdrH1nzJgx1o51reMi9iVJksQyZ87MpQYAAAAA3NKoWItjBw4csOeee86KFy9uDz30kE2ZMsU9v2fPHvd8iRIlrFKlSjZixAi7cuWK2zZ8+HB75ZVXrG/fvm57+fLlbdy4cb597ty505o0aWLFihXzvdd737x589yX2jRF7XwffvihlS1b1tq0aeNaN71tnmbNmrn3ej7++GP3Go1ZY1SLoN6n42zatMntM2wrqMY+fvx4q1atmhUtWtTtc9euXb596j2ff/651a5d2woXLmxPPfWU229k1IrYvHlz3z42btzoHuu4jz76qDtWw4YNXVWb58KFCzZo0CB78MEH7f7773fn/ccff4S7/y+//NJq1KhhRYoUcdV3K1assKj66quvrEGDBu5zqFu3rm3YsMG3bfXq1W6bxqf9Llu2LNT1Hj16tLu22q7jr1u3LtIx6X1Hjhyxnj17Wo8ePdy10Geg+6RkyZL20Ucfuef15c//up07d8769Onj7gd9vf766+566T36bPUZ6zhhW0FPnTrlXvvAAw+4Y7366qvuOfHG8cknn7j7Uddc2y9evBjlawkAAAAAQHxEsBaHFFi0atXKUqdObbNmzXKBxpAhQ1zApGApS5YsNnv2bBeMTJs2zRe6ydKlSy158uQuJFMAoxbPffv2uW3dunWz++67zxYuXGgDBw50gZbaP3UshU36Upumf8gzY8YM69q1a6RjnjlzpgtX9FodW2Pv2LGjC3i0f4VtahEMa+TIkTZx4kTXTqj35ciRw55//nkX5HgU3vXu3duFYidOnLChQ4dGOh61Inqhn46r4+v9/fv3t9atW7s53xT2vPjii/bnn3+61+l6Ll++3N599113PsHBwfbSSy/5gkv/+eh0LbWfJUuW2OOPP25dunSxkydP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AAAAAIDUhoo1IJWbP3++ZcuWLamHAQAAAABAqkOwBqRy+fLlS+ohAAAAAACQKtEKilRt+vTpduONN1qZMmWsWbNm9tVXX3mLpNojVclVo0YNq1Klir300kv25Zdf2u23324VKlSwXr162cmTJ/0cBw8etCeffNKqVatm1157re/z3nvvnfPYfvrpJ3vggQf8ehpf69atbfPmzb5NY7zhhht8/FWrVrXq1avbxIkTQ8f26dPHhg4dap06dbKyZctakyZN7L///W+01wlvBY3rXtRCunjxYmvYsKFv15i2b98e2r5u3Tpr1aqVlStXzm677TZ7++23Q9v0bPWMNZ5GjRrZ8uXLQ9t+/fVXa9++vd+rrj1kyBA7fvz4OT9DAAAAAACSEsEaUq3vv//eRo4caU899ZQtXbrUKleubI8++qgHZn/88YcHSjNmzPBwavTo0TZ8+HD717/+5T+/88479v777/t5hg0bZlu2bLGpU6fakiVL/Dz9+vWzY8eOnfXYNAZdt1ChQh5kzZ49206cOGGjRo0K7bNnzx5btGiRX3fw4ME2ZcoUmzt3bmi7jrn88stt4cKFHg4+9NBD9tdff8V63fjcy7hx4/w1hXF79+61MWPGhMajcOzqq6/2a3bs2NF69+5tGzdutN27d/vvCtbeeust69Chg4d/CttEQZraUXU/L7zwgodu4fcCAAAAAEBKRCsoUq2dO3daunTprGDBgla4cGEP1VS9durUKa+WUihUvHhx364A7p577rHy5cv7sQqPfv75Z/9ZoVW7du3syiuv9N8VLs2bN8+DpksvvfSsxnbkyBG7++67vSIsmP+sadOmHp4FIiIiPOy76qqrrHTp0tamTRsP01q2bOnbFao9/vjj/rOq0D744AMPBO+9994Yrxufe9F2VZWJqtNef/11/1nVablz57b+/ftb+vTprUSJErZ//36/F+2jqrrg2kWLFrUNGzbYq6++6uGd3gvdg561tr344ouWK1eus3p2AAAAAAAkFwRrSLVq1qzpAZLaEq+55hq76aabrEWLFrZ161bfXqRIEf+eJUsW/67qsYBeC6q41Gap6jZVWCls++677/x1VZidLYVpCq1UwfXtt9/6eVVhd+GFF0baR6FaQK2ZqjQLVKxYMfSzgi7dY9BKGpP43IuCr0COHDlCLZuqdNM1dK2AQjjRuD788ENv9QzoOAWXogq2vn372ooVK7zFtX79+n4uAAAAAABSMoI1pFpZs2b1aqzVq1d76KPWxlmzZnmlmmTMGPnjHx4YhdN8a2vWrLHGjRt7GFagQAG76667zmlshw4dsjvvvNPy5s3rc6BpTjMFXeHBWdTxqX1UFXgxbVc4FtM9nMm9ZMqUKdpjo14vnKrrFGCqvTW6Y+644w6vglOot3LlSuvWrZs9+OCD1qNHj1jHCwAAAABAckawhlRLAdIXX3xhnTt3tuuvv94ee+wxb1eMLSCKSpP9ay4yVXhpUn756KOP/LtaSs+Wwj7N86b5yILxfPLJJ5HO+ffff9uOHTu8jVXWr1/viwsE1GoZHqpprrM6deok2r0UK1bM99e+QcCn9lpV0qkyTc87vNpNIaGq/hS2Pffcc1avXj0P8/SlVlDN00awBgAAAABIyVi8AKmW2jk1Ub6q1hRQaY6wf/75x/bt2xfvc1xwwQVe+fbuu+/6OT7++GNfSEDOZfGCPHny+FhUwaXzaoyapyzqOQcMGGA//PCDT/avhRY0D1x4OKfwSpVuWpTg8OHDvspnYt2LKtL07DQfndppVQGoBR60sqrmilNLqwI0bVNgqEUgNKeaaIy6lsK/H3/80QM6WkEBAAAAACkdwRpSLS1AoMBJCwKoWmrSpEm+6mbJkiXjfQ6FUTpGwVaDBg181VBVwKmFMrxi7ExpLrIuXbrYoEGDvE1SIdXAgQN9EYFdu3aF9tN8ZAqtdB89e/b0cCugFlJV5GneNM3P9sorr8S6IMC53ovOPXnyZF/pU62rL730kv373//256z56fR8FdZpm1YS1aqgujd5+umnff64++67zxdfuOiii3zlUQAAAAAAUrJ0p86lnw1Aoli1apXdf//9tmnTpmi3K7QShWNpRYvBsywlmdC5YVIPAXHImDG95c2b3fbuPWQRESd5XkgQfK6QWPhsgc8VUgr+XiE1fa4KFMgZ5z7MsQYgRZg3sBUBCAAAAAAgWSFYAxJBs2bNbMuWLTFuVxtl5cqVefYAAAAAAKRgtIICieDXX3+148ePx7j94osv9sUVcGZo2UNCok0BiYHPFRILny3wuUJKwd8rJAZaQYE0JlgNE2lzjjXmVwMAAACAtIFVQZHq7Nixw0qVKuXf0yotbhAscDBu3DhfjRMAAAAAACQs5lgDUrn27dsTrAEAAAAAkAgI1oBULnv27Ek9BAAAAAAAUiVaQZFqvffee3bzzTdbuXLlrFOnTrZ//35/fc2aNdaqVSsrX7681a1b12bN+t/cXWqfHDVqlD366KN+XP369e3777+35557zlfxvOGGG2zp0qWh/X/77Tc/t/bVucaPH28nTpyI1/iOHTtmzzzzjNWqVctKly7tx8+ZMye0Xb9PmzbNGjVq5GN96KGHbPfu3b5t1apVPpbp06db1apVrXr16jZx4sRorxO1FXTevHl2++2327XXXuvHDho0KDRm3b/GFNx/7dq1bdGiRaFj//nnHxs4cKAfp68BAwbY0aNHfdvff/9tTzzxhFWsWNFq1qxpQ4YMsSNHjoSOHT16tL9etmxZH8+PP/4Yr+cEAAAAAEByRbCGVGvhwoUe5ih8+u677+yll16yzZs3W5s2baxKlSq2YMEC69q1q40YMcJWrFgROu7VV1+16667zt58803LkyeP779nzx4PvRR2PfXUU3by5Ek7deqUPfLII5Y/f36/lgKpt956yyZNmhSv8b344ou2cuVKD76WLVtmTZo08TDqzz//DO2jbR06dPBrHz582Mcb0JgUek2dOtUGDx5sU6ZMsblz58Z6zdWrV9vQoUOtZ8+efk2FavPnz7f3338/tM/rr7/uQd+SJUvs1ltv9fs9cOCAb+vfv799/fXXNmHCBL+ufh4zZoxv69evn++noFLb169f7+MSPV/dg/bVeS+88EJ78skn4/1eAgAAAACQHBGsIdVS9ZSqo1R5Va9ePdu4caMHT9dcc40HSyVKlLCmTZvavffe66FUQJVcrVu3tqJFi1rDhg090FKgVLJkSa+0UuWbwq8vvvjCfv31Vw/DdC5VcPXu3duDvPi46qqrbNiwYV6NVqRIEa98O378uG3dujW0T/Pmza1x48a+GMPw4cO92u6HH37wbREREf6aQjBV5ikAnD17dqzXzJYtm19TgVnhwoW9ck3PI7x6TNd68MEHfUzdu3f3qjNt130rjFPFWqVKlfy6Cs60Auq2bdu8QlDVfjpez13PRYGjwradO3dapkyZfN/LLrvMK92CxRUAAAAAAEipmGMNqZYCnEDOnDm9ZVEVawp9wlWoUCFSIKXAKZAlSxavrtJ3yZw5c6iNU+fat2+fh0wBVbIpiNq7d6/lzZs31vEpDPv000/tX//6l/3888/ecirhraRqqwwo6FIFna6bL18+D8kUzoUHgqoii4320b2MHTvWfvrpJ9u0aZP98ssv3qIZKFasWOjnHDlyhEI87aexKVALqD1WXx9++KHfu9pTw+k1HdegQQN77bXX7KabbvIgUfd+5513xjpWAAAAAACSO4I1pFrp059ekBkEY1HDn/AwK2PGjHGeJwibVKmmtseoFOTFRfO2ab6zZs2aeRuoWi7Vahou6lg0zmA8UbfpPtKlSxfrNT/++GPr0qWLX09zu+lntYOGU2VZVGp7je718HHpnt94443Ttl188cUe5mluOgWJCuFefvllrx5UK2vWrFljHTMAAAAAAMkVraBIU4oXL25r166N9JraK/X62ZxLraCqHlPbqL527Njh1WBxBVyiKjm1RD7++OO+SIJaToMQK6D21YAqv9RWqVbLYLEAXS+gOc2CbTFRkKf2UrVwtmjRwttb1cYZfs2YqGIuQ4YMkcak9k+10+pZaGy67+BZqHJv5MiRXt2nueR07Tp16niQt3jxYm95DdpaAQAAAABIiQjWkKZo7rQNGzb4ogZbtmzxOcBmzpxp99xzzxmfS+2ThQoV8rnc1FL51VdfeVCmCiwFUHFRW6eqt7Zv3+7H9urVy19XEBXQfG1aWEBhVt++fa1GjRqRWjV1PYVTy5cvtxkzZsR5H7qmgkSNV/OmaZ4zrTQafs2YqC1UlW6ao23dunUe5Knq7vrrr/eAThVwCgm1TYtFaHECrSKaK1cur6ZTyKZFDBQGauEIPafwewEAAAAAIKWhFRRpiibPnzx5soc8mo9MvytcUhXXmVJ4NnHiRJ+kv2XLlj7nmRYD0AIG8aGFB55++mmff0ztkqog0zkV/AVzlakaTCGgKuNq1659Wtum9lNYqGtrQYZGjRrFek2tYqrA66677vKgTOds1aqVXzM+FO4pWGvXrp23hqrSrkePHr5Nz1QrjrZt29bbVBW0adEHUYtrt27dfOVUBXlBC23u3LnjdV0AAAAAAJKjdKfi0wMG4LxTGKUgTHOwRbVq1Sq7//77vfIsrWgxeJalFBM6N0zqISAeMmZMb3nzZre9ew9ZRMRJnhkSBJ8rJBY+W+BzhZSCv1dITZ+rAgXinj+dijUAKcK8ga0IQAAAAAAAyQrBGpAIXnnlFV/EICZq2dQCAgAAAAAAIOWiFRRIBFqxc+/evTFu1/xm+fPn59mfIVr2kJBoU0Bi4HOFxMJnC3yukFLw9wqJgVZQII3RSpj6QtqbY4351QAAAAAg7Uif1ANAyrdjxw4rVaqUf0+MCfwXLFhgaZmerRYrSOj34fPPP7fNmzdbUli6dKnt2bMnSa4NAAAAAEBCIVgDUolLL73UPvnkE/8eH23btrU///zTzredO3fao48+aocPHz7v1wYAAAAAICGxeAGQSmTIkMEKFChgyd2pU6eSeggAAAAAACQIKtaQYJYtW2Y33HCDVaxY0QYOHGjHjh3z19esWWOtWrWy8uXLe2vnrFmR58pSq2e9evWsbNmy1qxZM/vyyy+jPf/atWutQoUKNn/+fP/9nXfesdtuu83KlClj9evXt/feey/eY1Vll1bm1DU7dOhgQ4YMsT59+oS2z54928eq69133322adOm0Da9/vrrr1vLli392o0bN7Zvv/02tP23336zTp06Wbly5Xzf8ePH24kTJ0L3evfdd1uXLl2sUqVK9uabb9rBgwftySeftGrVqtm1115rt99++xndS0ytoPp58eLF1rBhQz9v69atbfv27aF7kPvvv9/GjRvnP3/11Vf+/PVM9GyWL18eOreejb7uuOMOH+fWrVt9gYYnnnjC3++aNWv6Mzxy5EjomNGjR/vrOp+e4Y8//uiv33TTTaHvab3NFwAAAACQshGsIcHMnTvXnnvuOZs0aZL95z//scmTJ/scXm3atLEqVap4iNK1a1cbMWKErVixwo/RawpkOnbsaIsWLbLq1avbQw89ZLt27Yp07i1btvg+Ov7OO+/0+bl69erlrynQa968ufXs2dP27dsX5zgVLnXu3NnDPF1T4ZiCssAHH3zgYdiAAQNs4cKFHoApgNq/f39oH4VRGqeCsZw5c9rQoUND1ViPPPKIr/ipY5955hl76623/JkEFDRefvnl/rwUPA0bNszvb+rUqbZkyRKrXLmy9evXLxRMnguNU+fSc9YqpWPGjPHXg3BS29u3b2+7d+/2Z6lgTeNV2KggTWFbQCGdWjj1vhYrVszPe+DAAQ9KJ0yYYOvXr7fBgwf7vnp/58yZ49fTPV144YUeHsq8efNC3xWIAgAAAACQUtEKigTTt29fD6Gke/fu9uyzz3o11jXXXOOhl5QoUcLDtilTptgtt9xiM2bM8GqmJk2a+PbHH3/cK9Zee+01e+yxx/w1zQOm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WrWycuXK2f3332979+7119XGeffdd1uXLl2sUqVK9uabb0ZqBe3Tp48988wz9uijj/qxtWvXtkWLFkV7jbVr11qFChVs/vz5/vs777xjt912m5UpU8bq169v77333nm8YwAAAAAAEh7BGpDGHDt2zB566CErUqSIB2kKu+bMmRPavmbNGrv88stt7ty5VrNmzdOOf/3116106dK2ZMkSu/XWW+2pp56yAwcORNpny5Yt1rFjR+vatavdeeedtmfPHuvVq5e/tmzZMl/VtGfPnrZv377zcs8AAAAAACQGWkGBNOazzz7zQOvpp5+2bNmyWcmSJW316tX2119/+fZ06dJZ586dLUuWLNEeX6pUKXvwwQf95+7du9v06dPtxx9/tIoVK/prf/75p3Xo0MFatmxp7du399d27dplx48ft0suucQKFSrkr+s8mTNnPm/3DQAAAABAQqNiDUiDbaDFihXzUC2g9sxA/vz5YwzVRMcGcuTI4d8jIiJCr40dO9Z27tzpIVrg6quvtjp16li7du3s9ttvt2effdYKFy5sWbNmTdB7AwAAAADgfCJYA9KgU6dORfo9fNXPuKrIolshNPx8CtD69u1rY8aMiVQFN3nyZJs3b563nn744YfWtGlT27BhQwLcDQAAAAAASYNgDUhjrrjiCtu6dWukedESMuCqW7eu3XPPPXbxxRfbqFGj/LXNmzfbiBEjrGzZstajRw97++237dJLL7WPP/44wa4LAAAAAMD5RrAGpDHVq1f3UKtfv34eeGkBA63YmZAyZMhg/fv3t4ULF/piCLly5bJZs2bZhAkTbPv27bZy5UpvF73mmmsS9LoAAAAAAJxPBGtAGqNWTrVl7t+/39sxFXipwiyhVa1a1VcNHTx4sOXLl8/GjRtny5cvtwYNGvhrWhU0ulVHAQAAAABIKdKdijrZEgAkQy0Gz7LkYkLnhkk9BCSAjBnTW9682W3v3kMWEXGSZ4oEwecKiYXPFvhcIaXg7xVS0+eqQIGcce6T8byMBADO0byBrQhAAAAAAADJCq2gAAAAAAAAwFkgWAMAAAAAAADOAsEaAAAAAAAAcBaYYw1AipBcFi9g4QIAAAAAQICKNaQ4O3bssFKlSvl3nG7p0qW2Z8+eRHk0n3/+uW3evNl/XrBggdWtW5e3AAAAAACQZhGsAanIzp077dFHH7XDhw8nyvnbtm1rf/75p/9cv359mz9/fqJcBwAAAACAlIBWUCAVOXXq1Hm7VpYsWfwLAAAAAIC0ioo1pFjvvfee3XzzzVauXDnr1KmT7d+/319fs2aNtWrVysqXL++tirNm/W9urj59+tioUaO8qkvHqerq+++/t+eee84qV65sN9xwg7dSBn777Tc/t/bVucaPH28nTpyI9xhfeeUVP65ChQr2wAMP2Pbt2/31kydP2pQpU+ymm26ysmXL2n333WebNm0KHadW18WLF1vDhg3t2muvtdatW4eOldGjR1vNmjVDx/7444/+us4XfFer5rhx4+zhhx+2e+65x6677jpbvXq1j0fbAqtWrfLrBX755Rcfq8Zcp04dmz59ur8etH3ef//9ft6oraBqEdVxFStWtFq1avmz0n2K9n/sscfsqaee8u3VqlWzl156Kd7PEQAAAACA5IhgDSnWwoULPWBS8PPdd995UKNwp02bNlalShUPfrp27WojRoywFStWhI579dVXPWR68803LU+ePL6/5iSbM2eOB0UKfxQIqfrrkUcesfz58/u1nnnmGXvrrbds0qRJ8Rrf7NmzPVx6/PHH/fjs2bNb9+7dfdsLL7xgU6dOtb59+/q2QoUKWYcOHeyff/4JHa8wql+/fn4fe/futTFjxvjruheNVb8vWbLELrzwQnvyySd927x580LfFRrK+++/7wGd7ltBXGyOHj1q7du397HOnTvXBg4c6KHjhx9+GGr71Li0T7i//vrLw7+LLrrIr61n+Nprr4VCOVm+fLllzpzZ71cB3LPPPmtbtmyJ17MEAAAAACA5IlhDivXEE094UKRqsnr16tnGjRs9DLrmmmusZ8+eVqJECWvatKnde++9Xh0WCCrAihYt6oGT5iPr37+/lSxZ0qu/VPmmecS++OIL+/XXX23IkCF+rqpVq1rv3r0jhUWxUfilOckUcBUrVsxDKp3jyJEjHjopZFNlma6ra2TIkMHDvkC7du28suvKK6/0Crxvv/02NI9apkyZrGDBgnbZZZfZgAEDvBJP8uXLF/oetGkqeNPxV199dZytm5988omHZMOHD7crrrjCg0Y9m/Tp04fOnTt3bg/ewingy5o1q9+H7keVhLq/8OeuEFPPT89dIaJ+D+4JAAAAAICUiDnWkGIpVArkzJnTq61UsRa1KkstjaoeCxQuXDj0s4ImBU9B4KSKKjl27Jifa9++fVapUqXQ/qpkUzCmCrK8efPGOj5VY5UuXTr0u66jYEmhnc6rQDCgoEyBX7DipiiACuTIkcOOHz/uPzdo0MCDOYVyandViHXnnXfGOA5Vw8WXxly8eHG/XqB58+ZxHqdx614zZswY6bnv3r3b/v7779BzV3gYUDgXERER77EBAAAAAJDcEKwhxVIVVVRBMBZOYVj4vGjh4U9M5xGFPqpUmzBhwmnbFOTFJep1YhujaIzBnGRB2BadAgUK+Dxwn376qbdovvzyy16pt2jRojO6Xvh14xpzXGJ67uHnj+5+zudiCwAAAAAAJDRaQZGqqNpq7dq1kV7TYgZ6/WzOpVZQtUCqekxfO3bssLFjx1q6dOniPF77qz01oCq366+/3ltNVb32zTffhLapGk3zxMVnnCtXrvR5zLSwwKBBg3yRg61bt9oPP/wQr3Ep4Dp06FDo9/BFEdSyqsUL1B4b0Bx1Q4cOjfWcGrfGH1TVBc9dz04tnwAAAAAApEYEa0hVNHfahg0bfFEDtTVqovyZM2f6qphnSqtuqo1Sc7lpxc6vvvrK5zPTXGLhLY0x0XxtWjBAq5dqLJrQX+2Q+tLcawroPvjgA2+j1HnVyhosOBAbVYKNHDnSFzFQ0KfFDTQmhWL6Lgr0wsOzcGXKlPGFCBTEaUVQLaIQfs8K/TQfnMalhQ/URqvXJVu2bL4C6YEDByKds1GjRt4+Gxyne9YiB5rbLT5hHwAAAAAAKRGtoEhVNKH/5MmTPXhSYKTfNbF/fOYJi0rh2cSJE31C/pYtW3qodPvtt/s8afHRuHFj27Vrl1eVHTx40FciVZgmWlVTrylQ03fNRzZjxozQAgGx0YIC3bp181VKNYdZ0K6qRQXkjjvusEcffdRXI42OtmkV0WbNmvmxWmSgR48eoVZQnWvw4MG+8INCtl69enl1XBAW6tlu27bNrrrqqtA5NSebFioYNmyYNWnSxO9Dq6127NgxXs8KAAAAAICUKN0pJjkCkAK0GDzLkoMJnRsm9RCQQDJmTG9582a3vXsPWUTE/+Y3BPhcITnibxb4XCGl4O8VUtPnqkCBeMyvfl5GAgDnaN7AVgQgAAAAAIBkhWANOAuvvPJKqK0zOppzTO2UAAAAAAAg9SJYA86C5mzTXGcx0ZxjAAAAAAAgdSNYA85Crly5/AvnD3OsAQAAAACSm/RJPQCkbe+//77dcMMNVq5cOfv4448T9NylSpWyVatW+c979uyxpUuXWlLYsWOHj0Xfo44rNqqIW7BgwXkYIQAAAAAAOBtUrCFJaZ6ymjVrWpcuXSx//vwJeu5PPvnEcufO7T8/++yzpgVw69Wrl6DXONdxxWb+/PmWLVu28zImAAAAAABw5gjWkKQOHDhglSpVskKFCiX4uQsUKBD6WaFachE+rtjky5cv0ccCAAAAAADOHq2gSDJqddy5c6f17dvXfw5vl5Rx48bZfffd5z+rJfLuu+/2yjYFcW+++aZvmzhxoj3wwANWtmxZu+222yK1kwYtlzrPwoUL/StYcCBqO6bOH2zT6/r5qaee8mu9+OKL/vrs2bP99QoVKvi1N23adFb3HVx71qxZpy2AMGfOHLv11ltPawWN61737t1rjzzyiI/tpptu8nPrOvGh5/Pwww/bPffcY9ddd52tXr3ajh49aqNGjbLatWtb+fLlrVOnTvbbb7+Fjvn999+te/fuvn/VqlVt6NChduzYsdCzDMZbpUoVq1Gjhi1atMiWLVtmN954o1WuXNnPDQAAAABASkewhiSjVsdLLrnEg7UxY8bEuf+aNWvs8ssvt7lz53r7qEyaNMkaNGhgS5YssauuusoGDBhgJ0+ejHRc+/btvQVUX7pmfCjwU1CkkKhhw4b2wQcf2Pjx4/38CugUuN1///22f//+s7x783Bs165d9u2334Zee/fdd2NsV43tXnv27Gl//fWXB2oDBw60F1544YznutN9vvrqqx7cKVRcsWKFjRgxwgPFiIgID990PT2XNm3a2OHDh23GjBn+3q1cudJGjhwZ6b3avn27P2+N+emnn7bp06d72NanTx+bMmWKff/992f97AAAAAAASA4I1pBk1OqYIUMGy5kzZ7zaHtOlS2edO3e2kiVLhvZXRVWzZs3ssssu822qqtq9e3ek47Jnz25ZsmTxrzNpr+zQoYMVLVrUChYs6EFQx44dveKqWLFi9uijj3r7qirnzpbGcv3113uYJgrpVMlWv379aPeP6V63bNlin332mYdgCty0n6rXzsSFF15orVq1squvvtqr1RYvXuwBncanc2qOOl3n008/9Uo5BYKqOlNVXLVq1XxfhXqHDh0Ktd7279/fn99dd93lIVzXrl39XHfeeafPp/fzzz+f9bMDAAAAACA5IFhDiqEwRuFYOIVcgRw5cvh3VVclhMKFC4d+3rx5swdJarUMvjZu3Ghbt249p2uomisI1lQ1piAqphbOmO5VLal58uSxIkWKhLarffNMhM9xp3tSZZpWag3o/MWLF/fnoC+NJXwBhooVK/pYtm3bFnqvgoUXMmfOfNrz1PsYtI4CAAAAAJBSsXgBkgVVo0UVNSALAppwmTJlOu21s1mo4MSJE6e9Fn49bVfLqqqzwgUB19m65ZZbvO3yxx9/jLUNNLZ7zZgx4zkvzhB+r9E95+AZKHCLbnvw/ILvGlN83mMAAAAAAFIyKtaQLAShUdBKKOELGZyrqKGOrhd+Lc0HFhtVa2nCflWUBV+a8+ybb745p3GpDbZWrVq2dOlSb+dUBduZUmus2kjD7yF83rYzpco3BWPh96bFEX755Rd/DvpSVdu+fftC27WvjlGbKgAAAAAAaQXBGpIFzfF16aWX2ssvv+wBkRYN0IT4CSVr1qy+IIHmBpMyZcrYa6+95gGRWjCD1Tdj0q5dO5/YX6tbqt1RbaEKwxRqnSuFaa+88oqVKFHCQ6szpWO0mIMq6tSeqnnQxo4de9bj0Zx0LVq0sCFDhvicbzrnE0884QtNaIVPfSl869Wrl7ehfvHFF76vFj/IlSvXWV8XAAAAAICUhmANyUL69Olt2LBhtm7dOp+8f9myZdapU6cEO3/jxo198v077rjD2ya1oqYqrhQGaWGCbt26xXq8xtSjRw8PrHTM559/7itchs97dra0IILGFNOiBfHxzDPP+JxmLVu29BU4tchBdK2j8dW7d2+rXr26PxctaqD2z2nTptkFF1zgC05MmDDB99P1tCLpTTfdZIMHDz7r6wEAAAAAkBKlO3WukzMBSFJacVNtpDfccEMoTFM1narqPvjgg1Tz7rQYPMuSgwmdGyb1EJBAMmZMb3nzZre9ew9ZRMRJniv4XCFZ428W+FwhpeDvFVLT56pAgZwJu3iBWszUBgYg+VA1mdpAVVnWvHlz+/PPP+2FF16w2267zVKTeQNbEYAAAAAAAJKVMwrWZsyY4W1mjRo1sqZNm/o8S0BaV7VqVTt27FiM299++20rWLBgorbRKkgbOXKkz9WmlUrV8qrW1eXLl1ufPn1iPLZSpUreCgsAAAAAAM5DK+ju3bvtrbfesiVLlviKhgrY6tWr51UzQFqkxRZOnoy5FLVQoUK+YmZS0MqnqmCLSZYsWeziiy+2lIKWPSQk2hSQGPhcIbHw2QKfK6QU/L1CYkg1raD/d9ICPlG5/sG+cOFCW7x4sU/irknOtbohkNYk58pNrfCpr9QgOcyxxvxqAAAAAICzXhV05syZdtddd1nnzp0ta9asNnfuXG89e+2112zo0KFnciogSe3YscNKlSrl3xNa3bp1bcGCBQl+Xi1IsGfPniQdn47T8edK7amxtagCAAAAAJASnFHF2rfffmu9evXyeZmiVrFp7jUAiWPnzp326KOP2vvvv5+kj7h+/fpWp06dJB0DAAAAAADJRfozDdaihmqB1LYCIZCcnOFUiIlGc7Lly5cvqYcBAAAAAEDKC9YuueQS++KLL+zo0aOJNyLgPFq2bJndcMMNVrFiRRs4cGBodc81a9ZYq1atrHz58t76OGvWrNNaIrVoR9myZa1Zs2b25ZdfRnv+tWvXWoUKFWz+/Pn++zvvvOMhdJkyZbz667333ovXODWvYfA9aONcsWKFn6NcuXJ255132urVq0P7R0RE2OjRo61mzZoehmsOxL1794a2//jjj3b33Xf7OJo0aWIbNmyI1CL77rvv2s033+zbO3bsaPv27Yu2FXTdunX+nDQG3ZdWQA3MmzfPbr/9drv22mt95dRBgwbZiRMn4nW/AAAAAACkumBNIUHbtm39H9FXXXWVf1199dWJNzogkWmewOeee84mTZpk//nPf2zy5Mm2efNma9OmjVWpUsWDpK5du9qIESM8yBK9NmTIEA+cFi1aZNWrV7eHHnrIdu3aFencW7Zs8X10vIIvzY+mVmq9pkCvefPm1rNnz1BoFRuFVMF3hWkbN2603r17+3yHb775pt1xxx324IMP2i+//OL7Pf/88764yPDhw23OnDl+7aeeeip0PgV9HTp08GNz584daZvoeSiY0/yJ69ev97kUo9I527dv738DdC3dl8aksSnk07yLuj/dq0I1XTOpW1kBAAAAAEiyOdZWrVqVoBcHklrfvn1D7c3du3e3Z5991g4ePGjXXHONh0JSokQJD9umTJlit9xyi82YMcPuu+8+r/SSxx9/3CvWFEI99thj/tqff/7pwVXLli09fBIFb8ePH/fKz0KFCvnrqg7LnDlznOMM2i/1Xe2YL7/8sp+7UaNG/vr999/vY1BlncItBYb6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X79+Xt03a9YsmzBhgq1fv94GDx7s21asWGFz5syxMWPG+LO78MIL7cknnzzr9wUAAAAAgBQ5x9pVV13lFWqqbNmwYYPNnDnTrr766sQbHZCEguBY4ZUW6Hj44YetXbt2li5dOitSpIjdeuuttm7dOt93x44dljlzZg+c1NqpUGrfvn2hc1188cUeJunYtm3belCliq+SJUtGuqYCPFV0NWnSxH9//PHHPQxTtehjjz3mr2lV3ptvvtl/1ni6d+8er/s52zGWKFHCr9+zZ0+vWBOFf7fccouHewr/tDLw6tWr/VkF23UPOp+q/hTYFSxY0L8GDBjg8zMCAAAAAJCmKtb0D+K9e/f6XFOqXMmRI4c99dRTiTc6IJkoUKCAB0UKlnv16uUtmqrgUouk3HXXXbZ7925vd2zfvr199NFHkUKzwoULe2AVUAB19OjR066jCjG1S4ZT22l4dVuxYsVCP+u/QQXd8XG2Y9yzZ48HcGqBDSgou/baa31c+tJz0CImajHV19133+2v/fLLL9agQQP/m6FQTq20qni74oor4jVmAAAAAABSTcXa22+/bT169PCvwKuvvmpt2rRJjLEByYZaMZs3b26lS5f2Ci3NcbZy5Upbu3atb1dQ9MEHH/hr+tKcYmp7VPulRNcyferUqdNeU0VZVCdOnAgFeHK2K4ie7RijG1P4uPRdIdwbb7xx2j6qglOotnTpUvv000/tww8/9DZaLXqiltPw1nIAAAAAAFJlsKYqHa0COnv2bPv9999Dr+sf1G+99RbBGlI9zROWO3dumzx5cqS2zSAcU0ikdtH69ev7wgPffPONV4ip2utMFC9e3MO6oNVT9HvlypXP+R7OdowKzTQvmvZXO7ioSu67777zOec0Zs2vpmq3yy67zLerhXTs2LH2zDPP2BdffGG//vqrtW7d2urUqWOPPPKIV8398MMPkargAAAAAABIlcFa0aJF/R/RUekf6SNHjkyMcQHJiuYkUzj0+eefe8ukKrDeffddX5lTFCxNmjTJ8ubN69sVOGvhA/1+JjS3mRYCUIumQidVgW3cuNHnQztX5zJGjUtB2UUXXeR/D1566SVvE1VIp7noatWq5fPBadVRVb6pbVxBZK5cubyqTX8n1E6rORlV+apKtfCWVgAAAAAAUm2wduONN/qXJmu/8sorI207fPhwYo0NSDZU4aVFBLp16+aVWQrUevfu7St0Hjt2zO655x6v5nziiSds//79Pv/YxIkTz3jVXAVVf/75p4dYmg9NQZTmcou6yMHZOJcxak42Va0qMNN3zaOmij2FaqLgTKuTKoDLmDGjB20K2aRu3br+3FS9pnvSYghaOVTBGwAAAAAAKVm6U9FN9BSDd955xyte/vnnH2+BUyWKgjW1egFAYtu795BFRPxvvjngXGTMmN7y5s3O5woJis8VEgufLfC5QkrB3yukps9VgQI5E3bxAk12PmzYMK+g6dSpk33yySf2119/ncsYAQAAAAAAgBTpjII1zZdUtWpV+/rrr32+pq5du1qzZs0Sb3QA4mXdunWxLiJSsGBBn9sMAAAAAAAkUbCWOXNm27x5s8/3pPbP66+/3gM2AElLq3Vq1c+YaN4zAAAAAACQsM7oX9s9evTwSdVHjRplL774otWoUcPuvPPOBB4SgDOlFXq1Wmdq1mLwrCS79oTODZPs2gAAAACA5Cv9mex83XXX2fPPP+//iJ8/f7699957vjIigLP3/vvv2w033GDlypWzjz/+OEEfZalSpWzVqlVndaxWPL3vvvti3K5t2ic+tDLoggULzmocAAAAAACk6Iq1iIgIGzFihNWsWdNq167tr3Xv3t0uvvhie/LJJy19+jPK5wCEURWo/tvq0qWL5c+fP8U8G4VqmTJlSuphAAAAAACQZOKViI0ZM8b27NljZcqUCb02YMAA2717t28DcPY0T2GlSpWsUKFCliVLlhTzKPPkyWPZs2dP6mEAAAAAAJC8g7WPPvrIK9by5csXeq1AgQL2zDPPeBsbgLOjFsmdO3da3759/efff//dq0HVdq0VeIcOHWrHjh0L7b9mzRpr1aqVlS9f3vefNSvyvGPjx4+3atWq+bHz5s07o7H89NNPfm61pN5///22d+/e0Da1cd59991eVacQ8M0334zUCtqnTx//e/Doo4/68apsjWkxhbVr11qFChW8nRwAAAAAgFQfrGXIkCHalq+sWbPSCgacA4VLl1xyiQdrc+fOtTZt2tjhw4dtxowZXg26cuVKGzlypO+rFXm1vUqVKh50de3a1QPvFStW+PY5c+bY9OnTbfjw4TZt2jR744034j0OhXcPPfSQFSlSxM992223+fnCKdS7/PLLfZxqXY3q9ddft9KlS9uSJUvs1ltvtaeeeuq0VYO3bNliHTt29LGz8AkAAAAAIE3MsaZ2r19++eW0VQf1j2TmVwPOnqpAFVznzJnTK7l27drlwVXu3Ll9+8CBA61z586+Iq9ev+aaa6xnz56+rUSJEh62TZkyxW655ZZQMHfjjTf6dlW7NWjQIF7j+Oyzz2zfvn329NNPW7Zs2axkyZK2evVq++uvv0L7pEuXzscSU7uqFkp48MEH/WdV3Snk+/HHH61ixYr+2p9//mkdOnSwli1bWvv27fnYAAAAAADSRsWaKlkeeOABb+36+eef/R/z+ln/iNY2AOdO/10VK1YsFKqJQiktHrJt2zbfXrZs2UjHqKVSrwfHX3311aFtqi5TSBbfNlBdO3z/8DkVRQsrxDYHnI4P5MiRw79r7OGLNKjtVRV6AAAAAACkmYo1zZekyrRJkybZoEGD/Gf9o1utXrVq1Ur8UQJpQObMmU977cSJE6Hv0W0/efJkaB85depUpO0ZM8brP/Foj43a/h3d9WPbP+o569Sp43PHqcX19ttvjzRnIwAAAAAAKVG8/9WtAI0QDUg8xYsXt61bt3pLplbclG+++cbDscsuu8y3f/nll6fNe6bX5YorrrD169fbTTfd5L/v2LHD/v7773hdW8fq2poTTW2psmHDhgS9Py220LhxY19UYdSoUb7YAQAAAAAAqb4VFEDiq1Gjhi8e0KtXL9u0aZN98cUXNmTIEGvYsKHlypXLWrdu7WHX6NGjfX7DhQsX2syZM+2ee+7x4++9916f12z58uX2ww8/WL9+/eI9B2L16tXt0ksv9WPUUqoFDN55550Ev0fNJ9e/f38fu0JBAAAAAABSMoI1IJlQ6DRhwgT/WRP8a5ECVZ8NHjzYXytYsKBNnjzZPv74Y2vUqJFNnDjR+vTpY82bN/ftqgbr1q2bh3EK4RTUKZCLD7Vx6tz79++3pk2b2qxZs0KBXUKrWrWqrxqq+wpvYwUAAAAAIKVJdyrqxEqx0AqBUedF2r59u1fZAEBiajF4VpI94AmdGybZtZF4MmZMb3nzZre9ew9ZRMRJHjX4XCFZ428W+FwhpeDvFVLT56pAgf+bKumc51j77bfffBJyrQD60ksvhSYkV7WJVgZdtmzZuY8WAGIxb2ArAhAAAAAAQLISr2Bt7NixtmrVKvvjjz8itYdpUvVgonQAyZfaL48dOxbj9rfffttbTQEAAAAAQAIHa8HqfZMmTbJOnTqFqtVUuaZwDUDyNn/+fDt5MuZy2Ysuuui8jgcAAAAAgNTgjFKxq6++2po0aWKLFi2ybdu2WZs2bWzEiBFWrVq1xBshgHOWGuZBTKo51phfDQAAAACQIKuCjh492ttCpXjx4jZz5kwbOXLkmZwCQBp38OBBD+cBAAAAAEhTwZrmaLrssstCvxcuXDjW9jIAiGratGn2xhtv8GAAAAAAAGmrFfSKK66wf/3rX9a0aVNLly6dT3hesmTJxBsdgFQnWFUYAAAAAIA0FawNGzbMnn/+eXv88cd90YLrrrvOBg8enHijA5AifP311/bss8/a999/76F7lSpV/O/FJ598YnPnzrX8+fPbF198YR06dLDx48f7MaVKlbJNmzYl9dABAAAAADg/wVrOnDmtf//+Z381AKnOgQMHrGPHjta2bVufc/GPP/6wvn372osvvmjXXHONrVmzxlcT7tmzp2XLls3+/vtvf23cuHFJPXQAAAAAAM5fsHbVVVd5NUq4AgUK2H/+859zGwWAFOvIkSP28MMPW7t27fzvg1YgvfXWW23dunUerOm1zp07W5YsWXx/hWuZMmXyvx0AAAAAAKSZYG3jxo2RFjJYtmyZbdiwITHGBSCFUEDWpEkTX5RAfw9++uknb/GsWLGib1cbaBCqAQAAAACQZlcFDXfBBRfYHXfc4fMmAUi7du3aFfpbULp0aW8DVfVaIHPmzEk6PgAAAAAAkkXF2pdffhlpZT9VsEVERCTGuACkECtWrLDcuXPb5MmTQ6/NmDEjxtU/o7aTAwAAAACQJoK1sWPHRvrHcd68eW3EiBGJMS4AKUSePHns119/tc8//9wKFy5sS5cutXfffdfKlCkT7f5Zs2b1BQ527Njh+wMAAAAAkCaCNVWhAEC4evXqeTVrt27dPHBXoNa7d29f9VNzMUZ1yy232OzZs61Bgwb2wQcf+BxsAAAAAACkROlOxdSvFea+++6LtX1r+vTpCT0uAIikxeBZSfJEJnRuyDuRSmXMmN7y5s1ue/cesoiIk0k9HKQSfK7AZwspCX+zwOcKKUXGJPp/9wIFciZMxVrXrl39+9y5c311P60AmClTJnv77bft8OHD5z5SAIjDvIGtCEAAAAAAAMlKvIK16667zr+PHDnS5s+fH3q9XLly1rx588QbHQAAAAAAAJBMpT+TnY8cOWKbN28O/b5hwwY7fvx4YowLAAAAAAAASD2LF/Tp08fatGljF110kWlqtr/++sv+/e9/J97oAOD/Y441AAAAAECKDtZq1qzpq/j98MMPlj59ervyyistY8YzOgWAeFi1apXdf//9tmnTpjN+XlqJc9GiRdayZctzftYLFiyw8ePH+3/3AAAAAADgHFpBVaHWq1cve+CBB3ylUC1q8Mcff5zJKQAkMi0qMmnSJJ4zAAAAAADJKVgbOHCglSlTxt5//31buXKlVaxY0fr165d4owNwxtSmDQAAAAAAklmwtn37dq9Wy5Ejh+XMmdMefPBB+/333xNvdEAytmPHDitVqpSHzHXr1rUKFSrY0KFDvVW6WbNmVr58eevYsaMdPHjQ2zOfeeYZq1WrlpUuXdr3nzNnTuhc+n3UqFHebt2kSZPTwjEdW6dOHfv111/996+++sqvUbZsWWvUqJEtX7481EL65JNP2s6dO31sGmNctN+8efPs5ptv9nt47LHH7NChQ9Huq1Bd41PAXrlyZevZs2ekfRcvXmy33367rxh899132/fffx/aNnv27NBzUsXr2bS5AgAAAACQYoO1dOnS+T/YA/pHe4YMGRJjXECK8eKLL9qECRNsyJAhNmPGDHvkkUc8nHr55Zftm2++sfnz5/s+CuDGjRtny5Yt83BK+//555+h87z11lt+zL/+9S//by3wyiuveGClbQULFrTdu3d7YKdgTcd06NDBFxZR2KbQqm/fvnbJJZfYJ598Ypdeemm87uH555+3/v372/Tp0z0YVHVqVNu2bbPu3btb69atbenSpTZmzBj77LPPbO7cub79448/9gpWLXDy5ptv2rXXXuvjVKioOdo0V9uAAQNs4cKFVqlSJZ9Dbv/+/QnyHgAAAAAAkBTOaOUB/aNaVSiqRlFFzbp16zwcANKyhx9+2K666ir/Gj58uDVo0MBq1Kjh26pVq2Y///yz3XDDDXb99dd7FZt06tTJXnjhBdu6datdeOGF/todd9zh1WNB5Zm88847HkhNmzbNSpYs6a+9/vrrVr16dbv33nv996JFi9qGDRvs1Vdf9eBO1aQKvAsUKBDve1D1qSriROFY+/bt7emnn460z8mTJz18CxZFKFy4sI/jxx9/9N9VgdewYSSAg94AAQAASURBVENr1aqV/675GDNlyuTh2ZQpUzxk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rAEAAAAAkhtWBQUAAAAAAADOAsEaEtX7779vN9xwg5UrV84+/vjjszrHuHHj7L777otxu7Zpn5Rkx44dVqpUKf+emDTvW2xzv4U7ePCgLVq0KPR73bp1bcGCBUk6fgAAAAAAkjMWL0CiGjt2rNWsWdO6dOniE+InBoVqmTJlSpRzpyXTpk2zVatWWZMmTeLc99JLL7VPPvnE8uXLd17GBgAAAABAckSwhkR14MABXxEzMSfJz5MnT6KdOy05depUvPfNkCGDFShQIFHHAwAAAABAckcrKBKNWgl37txpffv29Z+//vpra9WqlbeFli9f3h588EH7448/fN/jx49b//79rWrVqlahQgXr1KmT7dq1K3QubR80aJBVrFjRqlevbq+88kqMraBqX6xXr56VLVvWmjVrZl9++WWkMb3++uvWsmVLK1OmjDVu3Ni+/fbbeN2PzqtrTZw40apUqWI1atTw1slly5bZjTfeaJUrV7ZRo0aF9tf4u3Xr5vtee+211rRpU38G0fn777/tiSee8PtThd+QIUPsyJEj8X7Wixcvtttvv92f7d13323ff/99tPt9+OGHPg49m/r169u7774burfx48fb6tWrvcUz8OOPP/r59KxUybZhw4ZoW0H1s8bQsGFDv9fWrVvb9u3bQ+fRM9Yz13V1vueffz7W9l4AAAAAAFICgjUkmvnz59sll1ziwdqMGTOsY8eOHkYtWbLEXn75Zdu2bZu9+OKLvq/CLgVgU6dO9eMOHTpkw4cPD51rzZo13u6pIOuhhx6yf/3rX7Z58+bTrqmASKGUrqV9FcJp//CQTiGcXnvzzTctZ86cNnTo0Hjfk8ahwEhjbNCggT399NM2ffp0D9s0l9mUKVNCodbjjz9uJ06csNmzZ/tYLr74Yt8/Ov369fPqvlmzZtmECRNs/fr1Nnjw4HiNSXPX6fg2bdr4PSnY0v0fO3Ys0n6ff/65de3a1cNEhWAtWrSwHj16eOilkK19+/YeaqrFM6D77NChg583d+7c9tRTT8U4Dj1XjUPvwd69e23MmDH+uu5L5yhdurQ/B4VvwfsOAAAAAEBKRrCGRKP5t9QyqPDqggsusIcfftjnWitSpIi3h956661eESWqfMqcObO3jJYsWdKDM4VfAYVSTz75pF122WXWtm1by5Url23atOm0ayrAUyWUqqtKlCjh4daV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bt36DaMLn9f53r17+jt+EhEREREREUVEEWKONSLfrF69WmLEiGH14owfP17QMV2hQgVeSJPEiRPLwYMHJV68eLwuREREREREFCExWKMIy9ZAKAJMQxgokSJFEldX19AeBhEREREREVGoYSso2Z3bt29L8+bNJVeuXFKyZElZtGiR5bNly5ZJsWLF9LO+ffvKhw8f9P0pU6ZIu3btpEGDBpI/f345evSot1bQS5cuSb169SRHjhz6/alTp1q+t27dOn1he0D7I1pDUcGG7bt16yZ3796VRo0a6d/169eXR48eWUK5GTNm6HezZs0qRYsWtezbv+PaAuf9ww8/SLZs2XRF1+PHj/vZFosVQ41VQ3FOXbt21euD45YrV052795t2RZjXbBggVSpUkVy5swprVq1kidPnnx1fJ+toK9evZKePXtK7ty59TyHDRsm//33n2X7CRMm6PvZs2eXhg0bytWrV20+VyIiIiIiIqKwiMEa2ZX3799Ls2bNdKL+lStXyqBBg2TixIny7t07/Xz79u0yd+5cDai2bdsma9assXwX4VHlypVl4cKFGu6Y9erVSzJlyiSbN2+WESNGyJw5c2T//v16LARoeKF11DB58mQZPXq0zJw5U3bs2CFubm76Wr58uYZQs2fP1u3Wr1+vx8M+MZ727dtrsHXhwgV/j2vN33//LWPHjpXBgwdryJc3b17p0qWLfP782abruHPnTg39ECzWqlVLOnXqJNeuXbN8jjG2aNFCVqxYIf/++6907NjR6j779+8vr1+/1nDTw8NDzp07J+7u7pbjYV+TJk3Sc02QIIEGe0RERERERET2jK2gZFcwp9fz589l5MiREjNmTEmfPr0MGDBAHB3/LyNG0JQ6dWr5/vvvpXDhwloRZkCYg/DLN/fv35fSpUtL0qRJJXny5DJ//nxJliyZBnjRokX7qnW0SZMmWu0FCMZwTGMOtrJly1qOi3nIRo0aJYUKFdK/cfxp06ZptVaWLFn8PK41+J6Dg4Ou5IrtEaqhes3WYC1OnDgaekWJEkXSpk0rf/zxh4aQvXv31s8RtlWrVk1/x7UuU6aMXLlyxc/93blzR3bt2qWVgLFixdL3ULFWvXp1DdAw3siRI+t48Ro4cKDcuHHDprESERERERERhVUM1siu3Lx5U0MshGoGhEBof4QUKVJY3kfAY7SCAsIrv7Ru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pHbS0aNHW/PmzX1/GzZs6Mflueee8+e64447bMWKFfG2rka2eCZ0bGK3gs6ePdtq1qzp+3P//ffb999/77f//fff9vLLL9utt95qxYoV89bPyZMnxzn2H3/80R+r59D9tQgDAAAAAADJHXOsIck7cuSIPfzww5YxY0abMmWK9ejRwwYOHOirg7Zq1cpuvvlm/75AgQI2f/788OMGDx5sO3bssIkTJ3oQp3Bn2LBhUb3m888/bxs2bLB3333Xg7AxY8aEt9199922aNGi8OqcCph0Xbfr+0cffdSuvfZan19MoVxk2DRhwgRbuXKlvf322zZt2jQ7cOCAvfTSS1Efi6FDh9p9993nz71v3z4P17Jly+bPdf3111vv3r2jep5oj82nn37qgWGzZs3svffes+LFi/sx136OHDnSFi9e7HPI6bgr4HzxxRdt586d/3iejh07WpEiRWzu3LnWp08fGzVqlC1ZsiTq/QYAAAAAICmiFRRJ3meffWa7d+/2ACpTpkweICnsUiiVNWtW69Chg6VKlcorsCLDml9//dXDuFy5cln69Ont9ddfj+r1FFi9//77HjipEksef/xx69Wrl39fuXJlO3HihFeFVapUycd3ySWXeBWagqg///zTevbsaRkyZLD8+fN7FZnGL1u3brV06dLZNddcY5kzZ7ZXXnnF7x+tatWqWa1atfz72267zf773//ak08+6fuvwK1NmzZRPU+0x0ahYO3atb0CLwjILr74Yvvrr7+scOHCduONN1rp0qV9m6rvFPz98ssvHvbFfr0aNWr4fit0VFCp1wYAAAAAIDmjYg1J3saNGy1v3rweqgUaNGjgLZcKdxQqBUqUKBH+Xm2YX331ld10003WunVrb+fMkydPVK93/Phxf+64njdt2rQean3wwQd+XV9VmXbRRRf5mPQaCtXieuy//vUvrxRTIKcqPAWBCt+iFRlGKczLmTNneP91PaiiO5loj42ORRAuBvuuNtjs2bP7MVA1ocJBVempFVR07GJTldvw4cN9v7t27eoVb3oOAAAAAACSM4I1JHlp0sRfWBkKhWJcVzVVQKGRgiu1dSoQUgtp7LnRoqXHR7rrrrvso48+8oDo448/9uvRjEnVdrp/v379PFgaMGCAB2yxHxPtsUidOu7/hSPDxsCxY8dO+dgkdOzVjqtqQd1HbaDxza8mCt4WLlxoLVu2tC1btnhr6dSpU+O9PwAAAAAAyQHBGpI8VVJpkv7IhQn69u3r861pIv3ICqkffvgh/P3YsWNt7dq1du+993qroybaD6rMEpIvXz4PwyIXLAgm7A9oXje9rloaVSmmRQCC4EytkGonjWtMmgtO87GpnVP7oLnGVq1aZbt27bIzKQjzIhdrUBvqqR6b3Llz+/xrAe2zKtM05kmTJvnCCVr4QMFi8P7EDglV1aa53xTgaeGF8ePHe9vqggULzug+AwAAAABwrhGsIclT+6Dm7FJV1c8//+yVYgp1FAYpzNFk+FpoIAipAtu2bfN50VavXu1hl4KcokWLnvT11HJat25dn4j/m2++8bnUYq9iqSotrcL55ptv+oqZQYWYArccOXL4hP8aqxYZ0DxoAQVuGu+yZcu8cmvOnDl29dVXW5YsWc7oMVPAp8BP49Pr6NhEhoPRHhutRKpFC2bOnOnhpo65gjO1h2qOOIWEen6tzqr510RVfJE0p5zaTnU89T4psNT9o3kvAAAAAABIygjWkOQpxNKKlX/88YdXWCmYUohzzz33eGCkoEZB2NKlS/1roF27dla2bFmfQ0y3Hzx40Fswo6FKrDJlyniFVefOne3BBx/8x320CqieU18jK8VGjBjhk/trrFp1s0mTJuHt+l5tk2qhVJWXwi7NPab52c4khYMKsubNm+eLD6jqLHIc0R6bChUqeLuoFiXQ8Vb1ncI6hXZaTELXtf9dunTxgLFkyZIxKvQi20YVgmoV0xYtWniFnxaEAAAAAAAgOUsVinZyJwA4jxr1mhjn7cNa1z7nY0HKkCZNasuSJaPt2XPAjh07cb6HgxSC8wqcW0hO+MwC5xWSizTn6Xf37NkvPel94p+ZHACSkKk9GhOAAAAAAACSFII1XHDatGnjbaPxeeGFF7zt8VxSe+u0adPi3d6qVSt77LHHzumYAAAAAABAwgjWcMHRnGGRK4zGdsUVV9i5prnO4prHLXD55Zef0/EAAAAAAICTI1jDBefKK6+0pCZr1qx+wcnnWGNONQAAAABAUsGqoEjxli9fboUKFQpf16qVX331lSU1M2bMsOrVq1tSPnYAAAAAAOD/EKwhxStTpox99tlnMeZY++WXX87rmJLrsQMAAAAAAP+HYA0pXtq0aS179uznexjJEscOAAAAAID4EazhrHvnnXesWrVqVqJECatfv759+eWXfvtPP/1k//73v61kyZJ255132oQJE2I8bvbs2VazZk0rVaqU3X///fb999/77Z07d/ZLJLUrqm1R1E7Zr18/q1SpktWrV8+++OKLcDujXu/XX3+1Ll26+HM0b97cevfuHeO5tPrmoEGDTrpfoVDI3nzzTX+94sWL++sNGTIkvF2vNXz4cGvRokV4Hz/99NPw9u3bt9sjjzxipUuXtnvvvdc2b94c9THdu3evPfHEE1a+fHmrUKGCtW/f3vbv3x/ePmnSJB+XKs40jv/973/hbbGPT6NGjWzw4MExnl/He9iwYf9oBd20aZPvj563atWq/t4GEno/TzZeAAAAAACSI4I1nFUKw1599VVfifP999/3YOWpp56ygwcPWsuWLa1cuXL23nvvWadOnTzImTVrlj9OAVS3bt2sWbNmvl3BVatWrezvv/+O6nXnzJljo0ePtldeecVSpUoVvv2NN96wq6++2rp27erPf/fdd9sHH3zgIZns27fPWx91+8lorOPGjbM+ffrY/PnzvcVUz7927drwfRS86bnmzp1rhQsXtueee85OnDjh29q1a+ffT5061Y+FnitaCsJ27NhhEydO9HDrxx9/9OMnH3/8sQd8eq2ZM2f6MW7atKn99ddfcR4fjW/hwoUxAr/Vq1f/4xgcOXLEHn74YcuYMaNNmTLFevToYQMHDrRFixbZ4cOHE3w/ExovAAAAAADJFauC4qxSdZiCrZw5c1quXLk8VFP1msKXK664wq9Lnjx5/L4KXVRFNXnyZKtdu7Y1btzYt3fs2NEuvvjiGOFQQu65555wpVVQySaZM2e2iy66yC699FK/3HHHHdazZ09fzECh0Icffmh58+a166+//qSvkSNHDnv55Zftpptu8usa69ChQ23dunVWrFgxv61KlSpepSetW7e2unXresCkCq6vv/7aQykdG73emjVrPKCL9rgq4NIxTZ8+vb3++uvhbaNGjfIQUsdZdIw/+eQTP+aqKIt9fLJkyWJ9+/b1eef0PihoLFq0qOXOndu2bdsWfl4Fjrt377aXXnrJMmXK5GPu3r27pU6d2oO6hN7PhMYLAAAAAEByRbCGs0rthgULFrQ6dep4WFOjRg1vPVTQo6oltRQGjh8/7qGXbNy40dsRI+f6UhVUtK655pqo7nfZZZdZ5cqVPdBSsKaqurvu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"/>
</div>
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
<h4 id="Brief-interpretation">Brief interpretation<a class="anchor-link" href="#Brief-interpretation">¶</a></h4><p>The top 5 categories hold the vast majority of the orders, indicating a high concentration of demand for these products which are furniture or lifestyle products ranging from health &amp; beauty to tech.
There is a long tail of products with significantly lower order counts, suggesting the large inventory of products that the store holds.</p>
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
<hr/>
<h3 id="Box-Plot:-Order-Value-vs-Number-of-Items">Box Plot: Order Value vs Number of Items<a class="anchor-link" href="#Box-Plot:-Order-Value-vs-Number-of-Items">¶</a></h3><p>The relationship between physical order volume and gross financial value is evaluated using a distributional lens. By plotting order_total_value against the discrete num_items variable, the workflow identifies how capital allocation shifts as consumers increase their purchase quantity. This visualization is pivotal for detecting price outliers and understanding the variance in spending patterns across different basket sizes.</p>
</div>
</div>
</div>
</div><div class="jp-Cell jp-CodeCell jp-Notebook-cell" id="cell-id=ebec9141">
<div class="jp-Cell-inputWrapper" tabindex="0">
<div class="jp-Collapser jp-InputCollapser jp-Cell-inputCollapser">
</div>
<div class="jp-InputArea jp-Cell-inputArea">
<div class="jp-InputPrompt jp-InputArea-prompt">In [18]:</div>
<div class="jp-CodeMirrorEditor jp-Editor jp-InputArea-editor" data-type="inline">
<div class="cm-editor cm-s-jupyter">
<div class="highlight hl-ipython3"><pre><span></span><span class="c1"># Configure canvas for distributional bivariate analysis</span>
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
<img alt="No description has been provided for this image" class="" src="data:image/png;base64,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REREZENBYhG//fabTJ48WTZv3iwxMTFyyy23yJ133qmOHT58WJ588knZunWr1K9fXx5//HHp3bu342dXr14tzz33nGrXoUMHmTp1qjRq1Mhx/L333pM5c+ZIZmamDB48WP2usLCwCp9bcnKGm/+3RERERERERGVLSIgSW4zQFxYWypgxYyQuLk7mzZsnzzzzjMyYMUMWLFggRUVFMm7cOKldu7Z8/vnncvXVV8v48ePl6NGj6mfxiOPXXnutfPbZZxIfHy/33HOP+jn4/vvvZdq0aaqz4P3335dt27bJSy+95OP/MREREREREVHVWCKgP3nypLRq1Uqefvppadq0qfTt21d69uwpmzZtkrVr16qRdwTkzZs3l7Fjx0rHjh1VcA+ffvqptG3bVkaOHCkXXXSRPP/883LkyBFZv369Ov7BBx/I7bffLv3795f27durzgL8bE5Ojo//10REREREREQ2D+gTExPl9ddfl8jISDWyjkB+w4YN0q1bNzWi3rp1awkPD3e079y5s0q/Bxzv0qWL4xhS6du0aaOOFxQUyI4dO0ocR2fA2bNnZc+ePV7+XxIRERERERH5WUBvNGDAALn55pulU6dOcuWVV0pycrIK+I1q1aolx48fV9+Xd/z06dOSl5dX4nhQUJDExsY6fp6IiIiIiIjIjixTFE974403VAo+0u+RPo/U+JCQkBJtsH3mzBn1fXnHc3NzHdtl/XxFVK9eTX0RERERERERWYXlAvp27dqpR4ysP/TQQzJixIhS890RjNesWVN9HxoaWio4x3Z0dLQ6predj5upch8fHyHVqjGgJyIiIiIiIuuwRECPEXnMeb/iiisc+y688EI11z0hIUEOHjxYqr1Oo69Tp47adlVkD6n1COqxjYJ6kJ+fL+np6er3VlRqahZH6ImIiIiIiMhr4uIi7BHQ//HHH2opumXLlqkAHX7++We1BB0K4L377rsqfV6PyqNoHvYD1p3HtobR/F27dqnfV716dTXij+Pdu3dXx9FxgHn0LVu2rPD5FRYWqS8iIiIiIiIiq7BEUTwE3ahM//jjj8v+/ftVYI+14u+66y5V6b5evXoyYcIE+eWXX2TmzJmyfft2ue6669TPIiV/8+bNaj+Oo13Dhg0dATwK7M2ZM0d+/PFH9XOYm3/DDTeYSrknIiIiIiIisppqRVgnzgJOnDghU6ZMkTVr1qhg+5ZbblFrzmPu+m+//SYTJ05US9Q1adJEBf69evVy/Cw6AJ577jlVuR7V8fF7GjVq5DiOYP+9995Tc+cHDRokTz31lGN+fUUkJ2e4/f9LREREREREVJaEhCixTUBvZQzoiYiIiIiIyGoBvSVS7omIiIiIiIjIHAb0RERERERERDbEgJ6IiIiIiIjIhhjQExEREREREdkQA3oiIiIiIiIiG2JAT0RERERERGRDDOiJiIi8rLCwUPLyctUjERERUWUFVfoniYiIyJTff/9NFi36VtatWy1nz56V4OBg6d69lwwcOFgaN27CZ5OIiIhMqVZUVFRk7kcCT3Jyhq9PgYiIbG7t2lUya9ZbKojPz8+XgoICqVGjhgQFBangfvToe6RHj0t9fZpERERkEQkJUedtwxF6IiIiL4zMz5w5XX0fGRklffr0l4SEOpKcfEKWL/9JUlNT1PH69RtypJ6IiIgqjAE9ERGRh82b96kgIa5nz94ycuRYNSqvDRkyTN599x1Zs2alanf//Q/xehAREVGFsCgeERGRB6Hw3fbtWyQ8PLxUMA/Yxv6wsHDVjjPhiIiIqKIY0BMREXmQrmbfunW7UsG8hv1t2rT9X/X7PF4PIiIiqhAG9KRwCSUiIiIiIiJ74Rz6AKeXUFq/fo2cOXNGQkJCpFu3nlxCiYjITUJDa0r16tVl584dqrq9q1F67N+582fVLjQ0lM89ERERVQhH6AN8CaXJkyfK7t07ZejQq2XMmPHqEdvYj+NERFQ1CNLbt+8kOTnZMmfO2yp4N8I29uN4hw6dpFq1anzKiYiIqEI4Qh/AI/OzZ8+Q7t17yR13jClVcXnu3JnqOJdQIiKqumuuuV4VvFu3brXs27dH+vYdIAkJiZKcnCTLli2RtLRUFfgPH349n24iIiKqsGpFLKd7XsnJGeJvMBqEkfgXXnitzPTPxx57QFq1aiOjRt3lk3MkIvInyHqaNestCQ4OVu+xBQUFUqNGDfUefPbsWRk9+h7p0eNSX58mERERWURCQtR52zDlPkAL4GHOfJ8+/cutuIzjaMc+HyKiqkOw/tRTz0nXrj1UIA94xDb2M5gnIiIis5hyH4DOnj2jCuAlJNQptx3SQdEOXyzSRERUdY0bN1FZT5jqhPfikJBQzpknIiKiSmNAH4CCg0NUNfvk5BPltsPcTrTDFxERuU9xNfuafEqJiIioSphyH6A3kliabvnyn0pVW9awH8fRjhWXiYiIiIiIrIcBfYAaOHCwpKenqWr2rpZQwn4cRzsiIiIiIiKyHla5D9Aq97riMpami42NUwXw9BJKGJlHMH/nnXezSBMREREREZFFq9wzoA/ggF6vR79o0beqmj2K32G+PNLsMTKP4k1ERERERETkfQzo3cSfA3rjUnasuExE5N33XBQpRV0TIiIiosoE9KxyTworLhMReR6zooiIiMidmHJfAYEwQk9ERN6uW1JHLR/KuiVERETkCkfoiYiILDIyj2C+e/decscdYyQo6FyC3JAhw9TKIjhev35D1i8hIiKiCuPEPSIiIg9D8VGMzDsH84Bt7MdxtCMiIiKqKAb0REREHi6Ah5VEkGbvHMxr2I/jaFdUVMTrQURERBXCgJ6IiMiDUM0ey4Jiznx5EhISVTt8EREREVUEA3oiIiIPwtJ0ISEhqgBeeZKTk1Q7fBERERFVBAN6IiIiDy8L2q1bT1XNPj8/32Ub7MdxtKtWrRqvBxEREVUIA3oiIiIPGzhwsKSnp6lq9s5BPbaxH8fRjoiIiKiiuA59BXAdeiIicv869IkqzZ7r0BMREVFl16FnQF8BDOiJiMhd69FjaTpUs0fxO8yXR5o9RuYbN27CJ5mIiIgcGNC7CQN6IiJy91J2qH4fEhLKOfNERERU6YDe9YK4RERE5NFCeaGhNfkMExERUZWwKB4RERERERGRDTGgJyIiIiIiIrIhBvRERERERERENsSAnshPC27l5eWqRyIiIiIi8k8sikfkR7gkFpG9qtwHB4eoAnlERERElcF16CuAy9aRHaxdu0pmz54hsbFx0qdPf0lIqCPJySdk+fKfJD09Te68827p0eNSX58mUUBjpxsRERFVFNehdxMG9GSHIGHy5InSvXsvueOOMRIUdC75Jj8/X+bOnSnr1q2WSZOmSuPGTXx6rkSBip1uRERlS0o6IdnZ2bZ8isLDwyUxsY6vT4P8ENehJwoQixZ9q0bmnYN5wDb27927W7UbNeoun50nUSB3uiGDxlWn25Ahw1SnG47Xr9+QnW5EFHAyMk7LY489IEVFRWJHmDr1+uszJCoq2tenQgGIc+iJbA5zcdevXyNDh15dKpjXsB9p+N9886WMHDlWqlWr5vXzpMrjfGv7Y6cbEVHZEAi/8MJrHhmhP3bsiMycOV3GjBkn9eo18NgIPYN58hUG9EQ2h8JaZ86cUXPmy5OQkKja4Ss0NNRr50eVx/nW/oGdbkRE5+fplHUE802bNuOlIL/DgJ7I5lAlOyQkRBXAK29ENzk5SbXDF9lrvjWyL4xFDtesWckihzbCTjciIiLyFAb0RDaHgL1bt54q0GvXrqMsWfKDSsHHSDyCdxwbMGCQOo7vmW5vfZxv7f+dbq6w042IiIjM4uK3RH5g4MDBkpaWKlOmPCG7dv2sRnTHjBmvHrGN/TiOduQf861xHO3IXp1uWHXCFexnpxsRERGZxYCeyE+UrgxbctuulWMDdb41ihier8gh2vG62gM609LT01Q1e+egXi8tiePsdCMiIiIzmHJP5AcwUhsfX0vGjfu7LFmySFWzL5lyP1CmT3+dy9bZAOdb+6fGjZuougeoi4AlJC+7rJ/ExcWrzJkVK5aqYB7H0Y6IiIioohjQE/lRBe1mzZrLqFHNVUo2AsOQkFDHnHkuW2cPnG/tv3r0uFSl33/++ccyf/5nJSo7YzkldL4RERERmcGUeyI/HNFF0BAaWrNEATzjsnVkXZxv7d8rF2At5IKCAhk+/DoZOXKMesQ29uM4ERERkRkcoSeyOY7o+h/Mo8bSdJhX7VwYj/Ot/W/lAmTX4FrjeP36DZl2T0RERBXGgJ7Ij0Z0hwwZ5rKQGito23u+NaZLIMMCy5rhOnO+tX+uXIBrjXajRt3ls/MkIiIie2FAT+QHOKLrn/OtMVqLAM+5yCGuN4un2bPOxflWLsC1HjlybInpMkRERERlYUBP5Ac4ouu/1xWjta6KHJJ9cOUCIiIi8hQG9ER+giO6/ksXOST/qXOBUXsE+jiG6wuYUoF2+CIiIiKqCAb0RH6EI7pE1q5z0a5dB1myZJFKwTdOoxgwYKA6ju+ZhUFEREQVxYCeyA9xRJfIWlD3YNWq5TJlypMSH19LzafHUpMYtUcgj2O6HREREVFFcR16cqR/5uXlqkciInI/PfJeVFT0vz1FJbY5Mk9ERERmcYQ+wGFtZFTRdk7/ZBVtIiL3wftsXFy8jBv3gCxZ8kOplQsGDBgk06e/xmXriIiIyBQG9AFs7dpVap1rrI3snP65Zs1KtQ42Cq2R/bgquEVEvl+2rlmzC8pcuYDL1hEREZFZDOgDeGQewXz37r3UjSWCPh0ADhkyTObOnamOYx1srndtH8y4ILLHsnWu6lwkJCSqdvgKDQ31wZkSERGR3TCgD+D0T4zMX3HFVfL++7NLpdxj/969u5n+aSPMuCCyz7J1rnDZOiIiIjKLAX0Ap3+2b99Jpk6dVGbKfadOXVS7kSPHsliTzTIugoLOvbSZcUFknWXr8Ho0vj61/Px8LltHREREpnFybQCnf27atF4FgC+88JoMG3at9Ox5qXrENvbjuE7/JHtkXDgH84Bt7MdxtCMi70Oh0fT0NDWdCcG7EbaxH8e5bB0RERGZwRH6AKQLpWH+ZnkB4JYtm9RSdkgVJXsU3HI18gfYz4Jb9sUih/aHWiQoNIpMGkxnwusRc+aRZo+RewTzOM6aJURERGQGA/oA9r/CyuSHBbdcYcEt+2GRQ/+CVUNQaBSZMs7L1nGpUCIiIqoMBvQBGgBixC8nJ1eleTqP0uv0z9zcXCkqKmTFZRsW3HI1osuCW/bCIof+CSPwZS1bR0RERGTbgP7EiRMydepUWbt2rVquZ8iQIfKPf/xDff/ss8/Khx9+WKL9k08+Kbfccov6/uuvv5bXX39dkpOTpXfv3jJlyhSJj49Xx4qKiuSVV16Rzz77TAU51113nTz00EMBvTa3DgBRFG/dutVlpn927txVtm/fwpR7GxXcateuoyxZ8kOpVQsGDBjEgls2wiKH/s/VsnVEREREtgzoEXTfd999Eh0dLf/+97/l1KlT8vjjj6sbnkcffVQOHDggDz74oFxzzTWOn4mMjFSP27dvl4kTJ8ozzzwjLVu2VJ0CEyZMkHfeeUcdnzt3rgr4p02bpkaeH374YalVq5aMGjVKAj0A3L17p0yc+IwsWbKoVPrngAEDZfr019X3HD2yPqTrrl69QqZMeULi4uJVJe24uFqSlpaiAvlVq5ar68iCW/5T5JDLShIRERGRJQL6gwcPytatW2XVqlVSu3ZttQ8B/osvvugI6BGAJyQklPrZjz76SAYPHizDhw9X2//85z+lf//+cvjwYWnUqJF88MEH6nd16dJFHcfo/L/+9a+ADugBgR2Wpvvxx+9VcGBM/ywoKGDFZRtCxxi+MjMzZcGCeeo61qhRQ2rUCFL7yR5Y5JCIiIiIbBXQI1CfPXu2I5jXEJjgC+n4TZs2dfmz27Ztk9GjRzu269WrJ/Xr11f7Mdp87Ngx6dq1q+N4586d5ciRI5KUlCSJiYkSqFhx2f9GdCMiIiU7O6tUsUNsIysjPDxCtcP8XbIuFjkkIiIiIlsF9Ei1v+yyy0qMUGHkvUePHmp0HqnCb7/9tixfvlxiY2PljjvucKTfuwrMkVJ//PhxNacejMd1pwGOB3JAD6y47B/wekEBNYzI9+zZW2VbIIB3zrhARgbajRw5ltMobFbk0BUWOSQiIiIiSwT0zl566SXZtWuXKmS3c+dOFXxccMEFqgjehg0bVEE8zKEfOHCgqsTuvE46tjEfHMf0tvEY4HhFVa9eTX35owsuaCZjx94jo0ff5ahmzznz9pKbe0bVh4iKilLXUc+5DgkpfgwOrqH2b9++VTIzM6SwMF9dZ7Kq6tK9e09ZsWKpDBs2vNQcesD1Rm2EHj16qetLRERErgUFVXM8BgUFblFs8l9BVgzm33//fXnttdekRYsWctFFF6k58RiZBxS++/XXX+U///mPCugRmDgH59gOCwsrEbzrAEa3xfGKio+PYJBLlpWfX/y33axZM0lIiHGM2usih3pFB3TeoIhkYmJsQK/yYAfXXz9CHnhgpXz44RxVA8R5Wcl//etttRLFddddK3FxET49VyIiIitLSSm+54+KCuNnJvklSwX0WG4OgTqC+iuvvFLtw2ixDuY1jNZjeTuoU6eOnDx5ssRxbGNePo4BUu8bNmzo+B5cFdgrS2pqlt+O0JP96UyUgwcPyaZN21Whw7VrV8vZs2clODhYjeJeccWVqvgkJCWlc4Te4uLi6sjYsePknXemy7Zt26VfvwGOZSWXLl2ignkcR7u0tCxfny4REZFlZWTkOB75mUl2U5GBG8sE9FhW7r///a+8+uqrctVVVzn2oyL9li1b5L333nPs27NnjwrqoUOHDrJp0ya59tpr1TaK4OEL+xHQo0AejuuAHt9jn5n584WFReqLyIqqVw9SgTvS6Z966nEVrGOE/lzF9LWyYsUytY12aJ+fX3ycrKtr155Sp059VchwwYL5JZaVxCoVKGzJ60hERFS+/PwixyM/N8kfWSKgR+G7t956S8aMGaOq0OtRdEC6/cyZM2XOnDkqxX7lypUyf/58tRwd3HTTTXLrrbdKx44dpV27dmod+n79+qkl6/Txl19+WerWrau2X3nlFRk5cqSP/qdE7of0+TZt2svWrZvUdl5enuMYCuLhS0M71kiwDwTtWJXAuKwkrx8RERERWSqgX7x4sQo6ZsyYob6M9u7dq0bp33jjDfXYoEEDFZR36tRJHcfj5MmT1fFTp07JpZdeqlL3Naw3n5KSIuPHj1drcl933XXyt7/9zev/RyJPysnJdms7sl6nTWhoTV+fBhERERFZTLWioiLmkp9HcnKGd64GUSUgrf7OO2+RiryUMbo7Z86/OcpLREREAeHXXw/JM888Lk899Zw0bdrM16dDZEpCQtR527DUNZHN5eXllgjmkZaNbBTAI7Y1tDOm5BMRERERkX1ZIuWerDHKizm6wcHnljkje9AF8AAF00aPvkd9n52dJRERkSqInzXrLVm/fo3az6QcIiKi8j9XeU9ERHbBgD7A/f77b6qK9rp155Y56969l6OKNlkf1iXXcN3ef3+2Ct6dq6LrgN7YAUBERETF9D2Rq89Q3hMRkVUxoA9ga9euUiO3COKNy5xt2LBWVq9eoUZ6e/S41NenSeeRnX2u0N3UqZMkPr6WDB16tSQk1JHk5BOybNkSWblymaE9Ru7Pv6YlERFRIN0TzZ49Q2Jj40p8hi5f/pOsWbNS7rzzbt4TEZElMaAP4F7omTOnq+8jI6OkT5/+JT68UlNT1PH69RuyV9ricP2MzqXUF7lMsUcaPtkL0z+JiDx7T4RgHhmKWCY0KOjc7fGQIcNk7tyZ6jjviYjIihjQB6h58z5VgV7Pnr1l5MixpT683n33HdUjjXb33/+QT8+Vyuc82o4R+K+++kItBYmieMZrC2FhYXxKbYLpn0REnoc0e4zM62De2ImKbezfu3e3ajdq1F28JERkKQzoAxA+qLZv3yLh4eGlgnnANvZv3bpZtUPgj+XOyB6c58hzzrz90z/RyRYXV0vS0lJkxYqlTP8kInITfEZizjzS7I8ePVLmHHpkMn7zzZfq/oj3RERkJQzoA3SZM3yAtW7drlQwr2F/mzZtZePG9WqZs5o1a3r9PKliMIpQcvus43uM0uPLCDcpoaHnlrIj66Z/tm3bXk2RWLjwK8fNZZcu3SUrK5PpnzbHaRRE1vkMxfvrqVOnZPLkiWXOoe/bd4Bqx89QIrIaBvRENoeUQAR6DRo0kkOHDpTZrlmz5nLkyGHVlqwNI0RhYeHy88/bXd5cpqenqeNM/7QfTqMgshadVv/TT4vUNMSy5tD/9NOPaj8/Q4nIahjQB6DQ0JpqrfmdO3eoJc9cjdJj/86dP6t2HM21NlwjZFts3bpJbeN64foZ59AjywLBfqdOnZkqaIORW6Tb4/qVd3OJESO0Y/qnfbCKNpE1P0OxOszJk8ly660jXU5DxH68fuPja/MzlIgshwF9gH54tW/fSQWAc+a8rQq8GD/AEAxif05ONgNAm8C1goSERJk8+UU1goA0wpCQUBXMP/nkI+pmxbjEHVkTrhteg1i9wDmYB12gCfUtMjMzmf5pE6yiTWTdTtS0tFRVL+jDD98t9b6L92Psx3HUMWFdISKyGgb0Aeqaa65XAcG6datl3749am4YgsHk5CS1bjk+3BD4Dx9+va9PlSpwM/LLL3tVEJ+SclKeeOJh6d27r0RFRUtGxmm1Bj2uJ46jHW9GrK1GjeK35UaNGpdb46JRoyaye/dOCQ4O9vIZkjuqaBuxijaRbztRUXtmwICB6v4H1eyLl/ItvifS05z6979ClixZxE5UIrIcBvQBqnHjJjJ69D0ya9ZbqsCW8zJnqOCK42hH9ihyiKyLZs0ukAUL5smXX37uOI6ChiNG/EWl3LPIofUVFOSrx8OHfyt3SgyOA25EOS3GPlW0y+ukYRVtIt/VoYmJiZVJk6aqzjdUs3euco+sRmxzDj0RWQ0D+gDWo8elUr9+Q/XhhZF6BPQYle/atYf68GIwby+//XZINm5cp75Hh4weic/NzZVPP/2PGm0ge9xcYtQ9KytLzZXHiC5kZ2dJeHiE+h77cRzteHNpnyraKGxYHrxGWUWbyLtw34OgHSPxqFGCaYh439XT1vA5ik7UN954WbXjknVEZDUM6EnRH1D8oLJnkUNAaiDExcVLv36XO6qiL126WKXc6+MczbX+zWX37r1k69bNsnr1ClWICSO8xuPYxhz7jh0v4WvWRiOAeD2WB69RjgASeR8GMVBoVHeiImNGf7YimMd+pN2jHRGR1TCgD2CsuOwfEOBhpBap16jUO3XqyyrNXhs0aIhMnPiQpKamqMCCnTbWh5vGVauWq+8RvBszLnRwj6kyvLm05whgWdMocJwjgETeh4zEO++8W2bPnlHmHHocZ+YiEVkRA/oAxYrL/gOBAIJ5wEg8gnfcjGCkHtu4GcEjIIUQASECDLKu48ePqgAe0EnjfD3ROYPjaMcbTPuOAGocASSy1jREV3Po+V5LRFbFgD5AOVdcxg2lnqPLisv2kpmZoR4xmoCl6TCSMH/+Z47jOnjXow1oHx0d47PzpfP7/POP1XWbMOEpVXV54cKvStxcYlWK559/Rj7//BO1TdbHEUAie7xOXc2hJyKyMgb0AV5xefPmDSp4SEo6N7czMbGOqorOisv2oJctwyh9WTce2K9H8ZF2T9aFzjW8Hlu1aiMXXthCfbm6ubz44lZq2TpmXNgHRwCJ7AEdqnoOPRGR1TGgD+CKy1h/ft68T9UHF4KHevXqy7FjR9X8sRkz3pA2bdqx4rINhIWFq0eMzOsU7csu6ydRUTGSkXFKVqxYqlK09XHj/HqyHmTKAF6P5d1c1q1bTwX0mEsfFRXt9fOkyuEIIBEREbkTA/oAhBFapNXv3LlDpWFPnvxiiSAPy5xNmvSoOo52XBbL2hDsRUREqsAO1xYjut9+u8CRot2xY2fZsmWT6shBO6YPWptemg6da+U5fvyYesQ1JfvhCCARERG5AytjBeiNpC7I9NRTU0uN2GIb+yEoKJgBoMUh5VqP6iJox3QKzJG/+OLW6hHb2A9op4utkTXhtYlpL8iUQeeaK9iP44mJdVngkIiIiCiAMaAP0Dm6OlD4v//7QG07H8d+yM3NKbEGNllPXl5uqSAdxfH27t2lHo3QLi8vz8tnSGahhgVed8iUcQ7qdQYNjo8YcQOfXCIiIqIAxpT7AKRHc1u3bivr1q0uc81VHN+162fO0bWJGjWC/rdmefGovTEjA/F+9erVpKCgwKfnSBWDyvWocbF48Q8ybtwoVQAPc+aRZo/XK67v5ZcPYoV7IiIiogDHgD6A5+hitHbSpKllrrn63/9+qNpxjq616ar1BQX5jm1UtMf1xXx5pHDj2upYnjUR7OGWW+6QFi1aqqXpUPwOX4A0e4zMc7k6IiIiImJAH+BzdPHoas1VztG1Dx3IG6dM6BR8PDpPqUCwHxoa6tVzpMpB0I4vXENk1kRGRnHOPBERERE5cA59gHKeo6srLutgnnN07ZVqb4TrWrt2gpoygUfnGgh63XqyVyccChzidUpERERE5LhP5FMRmDhH13/oCvbGgB3rzqMgHgJAbGNUXkP6PdeiJyIiIiKyPwb0AYxzdP2DcQQea9CfOnVKkpNPOI7VqpUgMTHRsn//L2ofl60jIiIiIvIPDOgDHOfo+ldAv3//PvWIqRO6KB6Cex3gAwN6IiIiIiL/wAmZVPyHoObQs1CaHTkvRYcUez3XWqfcG+Xnn0u/JyIiIiIi++IIfYD7/fff1LJ1WI8e86wR/HXv3kstW9e4cRNfnx5VACqfG0VFRUufPv0lLi5e0tJSZfnyn9Sc+rLaExERERGRPTGgD2Br166SWbPeUkG8TtvG44YNa2X16hUyevQ90qPHpb4+TToP58rnmZmZsmDBPDVyX6NGjVJV8JGGT0RERERE9seAPoBH5mfOnO4YscWIbkJCHTXXWo/o4nj9+g05Um9xeXm5JbbPnMlzfI+g3jklPy8vj1XuiYiIiIj8AAP6ADVv3qeqOFrPnr1l5MixapQXy58FB4fIkCHD5N1335E1a1aqdvff/5CvT5cqoGbNMMnNzan0cSIiIirOVtT3RM5ZcEREVsOAPgDhg2r79i0SHh6u5sq///5sWb9+jVqfPCQkRFW+x/6tWzerdrpaOllTaGhNdX0QrEdFRanAPTk5yXE8ISFRHcvIyFDtWPyQiIio7LpCru6JWFeIiKyKAX2ApmgjqK9Tp55MnTpJYmPjZOjQq0uk3GN0vnHjpnLo0AGmaFucrmSPm49Wrdqq2geQnZ2lplPgWs+aNV3Wr1+rRhvYOUNERFS6rtDs2TPKvCe68867WVeIiCyJAX0AQ7Deq9dlcscdYyQo6NyfAlLu586dqQrjkfXl5+erYB5Q0BBr0TtXucejnl+PAJ8phEREROdG5hHMY5Wfsu6JcJx1hYjIijgxKEBTtAEjtbfeOrLEBxdgG/v1SC5TtK0NI/HQunU79Zienibz53+mbkDwiO3i423VY1ZWpg/PloiIyFqQZo+ReedgHrCN/TiOdkREVsOAPkAhWMfceMyfxwivEbaxn3Pn7SE8PEI9InAvK50e+9PT09X3ERGRXj0/qjpkVeipMkRE5D54X8WceWS2OQfzGvbjONrh3oiIyEqYch+AULlVB+vr1q2Wffv2SN++A1TxNBRTW7ZsiUrR1kE/0rk5Sm9duNFAev3Ro3+o7fj4WurGIz4+XlJTUx3LEOJ4XFwtptvbCAs0ERF5/p4I9zmYM18e3COhHe+JiMhqGNAHIBRGQ+XW9u07yebNG1QK9ldffaHWK69Ro4YKEBHMX3JJV1XlHm3J2mJiYlQnTEhIqEye/EKJUfgrrrhS/vGP8Wr+fExMtE/PkypXoAlzONEZk5aWIitWLGWBJj/AZbGIrHVPhAJ45cGAB9rxnoiIrIYBfQBCQTQsw7J790554onJsmTJIpVGpgP6rl17yIABA2X69NdVO1ZFt35ggJHcGjWCVNB+331jpUWLlpKYWEeSkk6oDAy0wXG041QK+xRoatu2veqcWbjwK8cSSl26dFedcCzQZO+sC2RHnT17Vq1QgUJcXBaLyLf3RMhmQ+cpBjWcO9wwFRHHeU9ERFbEgD5A4eYRy7D8+OP3qtgLvvDhhRFeBPYoqIY52WhH1qbnVnfp0lWaNbtAFiyYL3v27FJfgHXp//zn4WpVg40b13MZQhtAwBcWFi4//7zd5RJKeG3iONqNGnWXr0+XTGRdzJr1lgridT0EPGJ1CqwqgiUne/S4lM8nkY/uiaZNe1V1om7cuK5UJyrviYjIqhjQB6jGjZuoNVUxyrd3724151rPodcBA46jHdlDSspJ2bJlowoABw0aLBEREZKdnS0rVy6TL774RBo3burrU6QKQICHwA8daz179i5zCSXcfKLdyJFjmUVjk5H5mTOnq+8jI6P+9557rpMGdS5wnMtiEXkf7nX69btcFi/+QY3IX3xxK6lXr74cO3ZUvc/iffnyywfxnoiILIkBfQDDSBBuHjHK9/XX85n+aeNlCDEtAiPw7dt3VMHCd999XWJ0ITMzQ7Zv36rascChtSFTBumduI46mDemf+ollFDfIjMzkwWabGLevE/VdBd00qATBkGDvqbopHn33XdUJw3a3X//Q74+XaKA63BbunSxdOhwieoMR9YMpiUimwb3SllZWep4nz4DGNQTkeUwoCdFz5PnfHn7QWCAKvcY4UPQXqtWbRUg6Cr3KKKG0XtAO15ja0OtA2jUqLEcPXpEdbihxoXuoMEcTqSHNmrUxHHDSdaGDhl0wISHh8vAgVepZUFLX9OrZOvWzaod61wQ+WYd+quvHiFLlvxQ4p4In7HY/8cfv3OaExFZEgP6AMYq2v4TLJw+fcqxffr0abVqAfbjRkQHiMXHTjFYsLiCgnz1ePDgfpk8eaK6yRw8+M8SHR2jrh+mUGAkV6fho7Aasy7sUeeiTp16MnXqU46VC4ydbrimmBaDTJu8vDypWbOmr0+bKKDWocfKP88++6TqJMWUJ8CjrnGBlX/QjtOciMhqGNAHKFbR9r8UbdyEILjDtvFGpbCweFsf5xq61qbT6hHURUdHqxGiL7/83HG8du0ElRKKjhu04xJK9vHrrwdV0IDrV3rlgiw1Ok9EvlmHftOm9WobRfH69h3gqHGxbNkStSwsjiN7hp+hRGQ1DOgDFKto+w89Ao9gHTBai+/1CD0CeQSH+jhTtK0N1yw+vpZachBBuw7i9TKEJ08mO9rGx9fmFAqb1LkABAMI2nF9nVcuwJQZHC9uH+rjMyYKrE5UdJzi9Yf58lg5xLkQ6Zw5b6usRrRjJyoRWQ0D+gDEKtr+maINWM8aqxNAdnaWGmnATQpWM8C618AUbeu/PnXNA9w4durURa1egEAe27jG2MYoUUpKMqdQ2IQOGFDjYsqUf5ZIqR80aIg8+eQj6hqzxgWR9+m6FbfffmeJYB6wjf34DNWdbkREVsKAPgC5qqJtxCra9mKcI5+Tk62WNHNeQxf7NY7QW//1qedv5ucXyP79+/43hz5ajdhjDj32A9ox/dMe11QHAuismTjxof+l9BYvFapTeoEpvUTer3Ghffjhu6Xui3C/hP3n2rPGBRFZCwP6AK+irT+0jMtiIeUX+1lF2x70nHlcN1S5Bz3Kh9F4FPMp3lddiooKVQDIglvWheuk0+yvv/4m+fzzT0rMoU9MrCtjx46TTz/9jxrRde6QI+u+52KZ0OPHj0pWVqYqXIkOmRo1aqhriNdsvXoN5OjRP9jpRuQDTZteoEbh9+7dLX369Hd0uGFKTHp6mjqOopVERFbDO8EATtE+fPg3OXTooFqiBR9iCP4weouU3gEDBqnjwBRte0CnjDG115hGiEcE82R9ubk56vHUqXR5551paqnB4cOvk7i4WpKWlqIqomM/AkE9tSIqKtrHZ00Vec/FKgVPPDFFveeiWrYO6Lt27aHec1999XnVju+5RN6tcYEO8RMnjsnEic/IkiWL5JtvviyxrOSAAQPlpZeeU+1Y44KIrIYBfQDCKDwCd1RVxrJY+MDSwaBevgVpvQgE0Y4FYOxRcEtznuPnvM2bEWsLD49wBHUYIZo8+cUSGRVXXjlUJk16VI0cAeokkD1WLsDI/I8/fqdSevGF7JqQkFAV2GOqDN6TuXIBkXchSMfqE1u3bpJFi75Ty9I5vz5RFA9T1zp27Mw6F0RkOQzoA/TDq02b9urDS88Pa9GipUrlTUo6Lvv27XEEgm3btueHF5EXIaBDAJ+bmyspKSnyxBMPl0r/TEtLU21r1gxTr2eyNlwjVM/eunVzuSm96Jzp2PESvucSedk111wv27ZtVpXs8fp0VeMCgxxoR0RkNQzoA5QukhYVFaWCgj17dqkvwIcY0n4zMjIkO/tcMTWyfkEfHRAWrz9fvGwdvtBpc649C/pYGa6bvl4xMdGqs82Y/tm5czfZs2enCurz88+yyr1NDBw4WNasWak6SVGQ1HhNkXKfmZkhP/+8XbUjIu9q3LiJjBkzTmbNektl0qBuiXHpVwTzo0ffo9oREVkNA/oAhA+pX37Zq+ZuImhHmmfLlq3VckqowIwRerTBcbTT87DJmvR0CQ3BoL5euHbGYF7vI+uvQtGmTTvZuXOHCgI1BIB6Wx9nlXt7QCCAJSWxhGRsbJxa2xr1ETDyh7oIGKHHcQYMRL6BLBoE8J9//rEkJZ1wfL7GxMTKiBF/UXPpiYisiAF9gI7o4kMKQR9G/3BDqUfn9Qg9bjR1MM8RXWszBuwXXXSxpKenS3Jy8c0Irl9CQh2JjY1V19NVBwBZb741Rm3DwsId6fTGa6b34TjascaFvQIGVLpftOhbWbjwqxJFtzAyz2CeyHeQbo8ReozI431Wj9DrAqXYxmuYiMhqGNAHMD0CjxtK44cXKjFjOazq1Ws4qjOTdWGutYbrGR9fq0RVdMzP1cG8nm4REVFceI2sB6/B1q3bycaN66Rnz96qQJOuZo9UbbxO3333HTVSzwJN9oOgfdSou0oU3WIGFJFv/f77byqYx/urMStRrxKD/TiODjl2vBGR1TCgD9ARQGNqNgoxoUBTfHy8pKamqgDwzJlURzDPEUBrQzqga65T65HuS/agp0egLkJ0dIz6Xt9wAmfC2Ffx8lclV6ggIt+YN+9TRyYUlgHt3buvREdHy+nTp9WqP5iOiOPz538q9933EC8TEVkKA/oAZBx1R5CAtHtj+ucll3SV3bt3qjQz4JrI1uYc1GEu7vz5nzm2naugYwkeBIhkTbhp3LVrh3Tp0l02bFirsitcVUTH8e3bt7DGhY2vM0bo0cHKlQqIfPtaRIV747Q1FMXTMG0N+/FejJUqWFeIiKyGd/UBqEaNc5cdQTvmjWkI6o3bgPlkZI/r6WqOvPM2r6e1IcjD6xAda3/+8zVqvrWxIrqeb33kyGGVls+iePZL7cU1Xb9+DefQE1mkrpAO0hG0o4OtVas2Uq9efTl27Khaxg51aXT6PesKEfkeO8VLYkAfoAGDGQgYsC42WZPZOgfMuLBHUTzcQPbseWmZ8623bt3Eong2g85SXeV+6NCr1cgfrjOyLlATAVXuWXSLyLt0p3dxEdlEmTz5xRL3PKhTM2nSoypDSrcjIt9gp7hrDOjJ0etc1jbZoyZCRbEmgrVhdAij8AjysLQZpkc4z7dG/QscRzsWVLPPTQiC+e7de6kOGuO0F1znuXNnquMsukXkXcYpL089NbXUAAa2sX/8+NFqm++5RL7BTvGylZxcSwEZAOLD6eKLW6ngAI/OH1YMAO0FVe6Rqn3ddTeqR2yTvSClHvPkEeQZlyUEbGM/jqMd2QPS7DEy7xzMA7axH8fRjoh8M23t3/9+X73HYtReL/GL7Y8+es/RhtPWiHzbKf7CC6/JsGHXqixGPL7wwmtqP46jXSDiCH0AwoeUsecZKfWYI2bsrcZ+vRwa5ouFhYX55FzJ3PVE4R7URViwYJ5jX2JiHbnwwotl//7ipes4/8/6sCwS0q/x4YTXpquieDjO5ZPsAUEB5swjzb6sgpTYj+uMeglYqpCjgETekZub4/geU182bdqgprKhgCyW90XAf+ZMnqMNlhBFJXwislan+N69u1U7TFUMNAzoAxACOldrmBtvPo378UHGgN768//CwyMc683raRN4TEo6ob5wHDcinE5hD5hLjfTrsoriMZi3D13oEHPmy4NOG7RjoUMi78Fno5ExeEdQjy8jLPVLRN7DTvHzY0AfgMymi5mdo02+mf+HYB0Q9OmbEBzDCAMCBH2cI3/2gaC9rKJ4ZM9Ch+VBBgbacZoTkfdgdA9T01JTU87bFu24zCSRd7FT/PwY0Acgs2uQ88PL2ozF0mrVqi3PPvuSCgh0AIiMjCeeeFhSUk7+r32oD8+WKsO5KB7Zv9Ch85I7LHRI5DvIjjEG9MYsN2NWG9oRkXexU/z8GNAHoGrVStdCrFkzTKKjo+X06dMl5pNVpgOAfCclJUUmTnxI+vYd4JhzvWzZEklNTeVlsTGut2p/mCaB+bnTpr2qUnY3blznmEbRpUt3ycrKZKFDIh+9v+7fv8+xjQ62Fi1aqvozmK62b98ex9Q2tNOBPhH5rlPcWX6Ar/7DSC0ApaWVDu4QxDsH8sb27JW2R1E8kSIVGHz11ReOgj7Fb3znRhhYFM8+uN6qf02f6Nfvclm8+AdDwFBXkpKOq6V4EDBcfvkg1kYg8jJkyuDzEkHAqFF3q8/PPXt2qS/A6xSVtOfMmaHascYFke86xbHKj3NhvHyu/sOAPhC5GqEvD4JCsr5mzZrLb78dcnkMAUSTJs3k0KEDXj8vqhyut+p/nTNLly5WgTw6SY0BAzpM4+Li1fE+fQYwqCfywT0Rpqxdeull6gsBAurOREZGOaYdzp//qZw8mcysRSIf4Oo/NhihP3HihEydOlXWrl2r5vcOGTJE/vGPf6jvDx8+LE8++aRs3bpV6tevL48//rj07t3b8bOrV6+W5557TrXr0KGD+j2NGjVyHH/vvfdkzpw5kpmZKYMHD1a/ixXbyZ9gbjVuOE6cOCZPPDFFliz5QdatW+0oite1aw8ZMGCQvPTS1P/NxeYcejutt+rcE410M/RQ4ziq4LPavT1gtYKwsHCVsovgffjw6yQ+Pl5Nh1mxYqnaj2rbgbrkDpGv6OzEjIzTKpDH+63zZyX24zhw2Toi3+DqPxYO6DEX6b777lPzt//973/LqVOnVNCON9NHHnlExo0bJy1atJDPP/9cfvzxRxk/frwsXLhQBfdHjx5Vx++991657LLLZPr06XLPPffIV199pVKnvv/+e5k2bZq89NJLUqtWLZkwYYL6ftKkSRLIioqK54JVlPOSLWQteK20b99Jtm7dJPPnfyaRkSWX1EEqL0YWcnKypWPHzgE5t8huuN6qf8FrEJ1sCAp69uxdqpMG69OjkwbphGjHdeiJvL9sHaajlVfjQi/5y2XriHyHq/+4Zi732gMOHjyoRt+ff/55ueiii6RLly4qwP/666/ViD1G3idPnizNmzeXsWPHSseOHVVwD59++qm0bdtWRo4cqX4Wv+PIkSOyfv16dfyDDz6Q22+/Xfr37y/t27eXZ555Rv1sTo7rueKBIiYm1lT72Ng4j50Lucc111yvAvXt27eoVO0LL2wh/fsPVI/Y3r59qzqOdmSP9Vb79OnvCPqwD7USdGEm7MdxtDNWYCbrztE9e/asRERElArmAdvYj+Noh0CCiLwDrz8UwINt24o/Q5s3v0gGDBioHrGN/Xo+PVf+IbLO6j8cpLLICH1CQoLMnj1bateuXWI/UuS3bdsmrVu3lvDwcMf+zp07qw4AwHF0AGhIpW/Tpo06jv07duxQI/oaOgNws7Rnzx7p1KmTBKqyit+VBellZjsByHeCgoJVVd7du3f+ryhesJw5UzyyQPZab7W8oniYd419LNBkfTVqFH/UNmrUpMz5t9iP43jdBgcHe/kMiQIbVob59NP/qPdYZLIh4w2vRT1Cj2281/bt29/Xp0pEZL2AHqn2SJfXMAL10UcfSY8ePSQ5OVkSE0uu+YnU+ePHj6vvyzuO5deQHmU8jhum2NhYx88HKrOjP0y5tz4EffHxtWTcuL/LkiWLSsyh79YNc+gHyvTpr3N+ro3WW928eYOqqowMGaRkI8BPTj6hlmVBananTl1UO3yRtRUU5KvHw4d/d8zRdYb9hw//pr5HxzNrXRB5z7FjR9VoHzKhkG5vXLYO27g3xXG0IyKyGp8H9M4wx33Xrl3y2WefqYJ2zjer2NYBKVLnyzqem1u8lFd5P19R1atXU1+BOoe+qKhAgoJ8PjuDzpOi/ec/D1dTT/A1atQYycpChd5IxyoF/foNkAUL5suYMXczRcnSqkubNu3UTWSvXpfJ6NF3lQgAhw0bLrNmvS2rV6+QSy7pIsHBXIXC6qpXr6muIebhvv/+LBk1amypJXfee2+mes1if3g40wiJfPEZWrduPfnss49LrEJRp05due66v8jx48f4GWpTQUHVHI+8nyV/FGS1YP7999+X1157TRXCwwhFenp6iTYIxmvWrKm+x3Hn4BzbGPXXoxuujputch8fH+FXAVBe3rn0efy/0Mmhi70Yn1c9NzchIVbi4oqLxpD1oPMK16tZs8aSlnZCFYVcunSpYySwX79+MmzYMGnatJFqFx4e5HgNkTWFhBS/NYeE1FCvPefgLzi4uIMNwTxfm/aA1yHqu6xZs0r27t0tgwYNkrp166qMsR9++EFVu0cHXPfu3SU+vmRhSyLyzmcoXqeDBw9U23hNYjqofv/96aef+BlqUykpxff9UVFh/Mwkv2SZgH7KlCnyn//8RwX1V155pdpXp04d2b9/f4l2J0+edKTR4zi2nY+3atVKpdYjMMU2CurpG2F0EGDevhmpqVl+NUJ/5sy5IloI2hHMI7DH93g0BveQm1soaWlZPjhTqujoAjplli9fKevXry1xDH/zWB0CX0i9R7vs7HzJyeH1tPL13LJli7peK1askB07flbZFZgzn5ycJEuXLpH09DR1fMuWzZKamulXHY7+ql+/gSogaNeug1rbGkVdjXURMjNPy44d21U7vt8Sef8z9NCh3yU2dqd8//1CWbfuXN2S7t17ypVXDpFffz3Mz1CbysjQSxPm8P2VbKciAzeWCOixtNx///tfefXVV+Wqq65y7Me68jNnzlS9p3pEcdOmTaownj6ObQ0p+EjXRyE8zB1u166dOo4RD0CxPPS0tmzZ0tT5FRYWqS9/kZ9fOuVej8a7qpiN9q5+hqyjdet2pYJ5ZziOYj8FBbjG/vP37G8whxM3kh07dpGhQ4erugeYKuFcFO/IkcPqmmZn53K+tQ00aNBY7rzzbpk9u7guwpAhw9R69GlpxevQo5MGx9GO77dE3oX31e+//1bmz//c8PqsJWlpKer1uXr1SgkLC1ft+BlqP/n5RY5Hvr+SP/J5QH/gwAF56623ZMyYMSpQR6E7rVu3blKvXj21fjzWl8foxvbt29XydDBixAiZM2eOCvqxNB3WoW/YsKEjgL/55pvVmvNI38eo/tNPPy033HCD6ZR7f2O2yF1+/lmPnQu5x4kTxxzfo6o96iTgOmP+fLVq1R3X0NiOrF0UDwXwGjRoqPbp5er0I2C0nkXx7KVHj0ulfv2GqpNm4cKvSnXSYH1dIvI+ZM6sXLlM4uLiVEG8b775UhWnxIoTqHK/Z89OSUtLU+2IiKzG5wH94sWLVeAxY8YM9WW0d+9eFexPnDhRrr32WmnSpIkK2uvXr6+OI3h/88035bnnnlP7sRQdHnX66dChQ9W69AjqceOEOYsPP/ywBDqke3qyPXkXgjxj5d3CwgJ1Q4JCPidOHFdL2Glop6dWkDUVr0zQUxYt+k7mz/9MBXzGDJoNG9bKqlXLJSIiUrXjtbQXBO2jRt2l1p3HEoUhIaG8hkQ+tmPHNlXFHkE7VhHR76uYtoZtwHG0w/suEZGV+Dygx8g8vsqCIB7L2JWlb9++6quyvz9QAwYzGDBYGypnaxdddLGqE2Gs0IvlzlBT4pdf9jqmpoSHh/vsfKnio0WAwB1rJOtl65YtWyJ5eSmSmZnB0SKbvw8jQCAi33eKr127SgXv+rWps6HQiaq3MR0K7UaOHMv7IiKyFJ8H9OR9OTnZptqjhkGgT1OwsszMcwH9wYP71fy/4cOvk/j4eFWlF/P/sN/YAcCA3tpQCb10Z9q5uge6iCXacbSIiKjykCmjg3nAZ2ifPv0dn6HLl/8kqakp6hjaIeNTr6RERGQFDOgDEOaFmWtvfqk/8h5jcI7gDqMHxmXOhg69Wt599x1H2mB4OJcgtDKMBG3fvkVd14ceelyWLFmk5nMa51sPGDBQXnrpOdWOUyiIiCqvRo2gEnUuMCXG+TN0zpy31eg8YF49EZGVMKAPQDVrmgvOGQBaG4I8zXnJQVf7USiPrAtpnQjqsXJBs2bNZdSo5i7nW7dp01Y2blyvrq1eBYSIiMzBe6t2++13lgjmAdvYrwN6dK7yPZeIrIQBfQDKzS1ej9NYVdv4gea8nZ2dJdHRMV49R6o4XC9t8+YN8vDD90n//lc41i3/6acf1ZJYrjoAyB4435qIyDOMq4d8+OG7qgPVGNQjzR77NVfL+xIR+RID+gBPLwNj8O5qG8ugkXUVFJyb+wcI3ufN+7TcKRec/2ddKJSGAH7nzh3qRtJ5tAiwf+fOn/8X6HMuJxFRVQsF470Wo/B79+5Wc+h1pzjm0Kelpap7J3zeslAwEVkNA/qAxN5lfxuhx5w+BHnljRzgJgQ3LByht/7NZfv2nWTr1k1q3qbzfE5cZ+xHcctOnTrz5pKIqIqdqPh8xHsr3nsjIyNL1C3BOvRYVWT79q2qHTtRichqGNAHoMoUxRPhMmdWDgC7d+8lGzeuUysSlAU3Ibgx4eiC9V1zzfWq4N26datl3749arQoLi5ejRLp0SJc9+HDr/f1qRIR2RreSzt0uER1ou7YsVW91w4ZMqzUey6gHT9DiawxVQbxCQa1qptcjtsfMaAP8DnXnmhPvlu3PDo6WkJCasrJk0mOY7VrJ6pCaxkZp7luuU00btxERo++R2bNektNoZg//zPHMXxw4YYSx9GO7Ik3I0TW6kTdtm2zynLD0q4LFsyTgoICVUQWGVJ6NRG0IyLf+f3332TRom9l/fo1JVb/GThwcEDfEzGgD0hMufc3O3ZsU2mDp0+fFpHTjnXK8aiDexxHO65bbi96OoXx5tJslg1ZB29GiKwHgcCYMeNUJ6or6EhlJyqRb6HGxezZMyQ2Nk4tJ5mQUEeSk0+oLBoszXznnXerpScDEQP6AFTW0mZlOXMmr8Ra52S9kT68ySHgAyxthsI92MZNCAr54BriC+2wTj1TBq0f9OFDCx9MqLiM66iXrcN1nTt3pjpev37DgO6RthvejBBZF95v8Z6K0T9Md9KfoV279gj40T8iq9wXYYqp80oUQ4YMC/j7Igb0RDaHQA8juPqGBEXUEOSfOpWuejERvKOIGoIJtEOKEov6WBtuKHHtjB9ayLAAbGM/KjGjHa43WR9vRoisDx2keE/Fe6zuRGUHOJE174u0IN4XCasIBGgKr7n2nENvh2UIcV1RoXfixIdk7Njb5ZFH7pcxY25T29ivlx80e/3Ju9AZg7lhKITnask6wH4cRzuuiew/NyM4jnZE5FvFS4IWV78nIt/ifZEXAvrs7Gw5cOCAbNu2TX7//XfT6dxkj5R7sq7iVQiKlzObOXOanDyZLK1atZEBAwaqR2xjv16vHiP0ZO3riWuEuWHlwRrJaMfraX28GSEiIqoc3hd5KOUeN5CfffaZLFiwQHbs2OGYuwso2tSlSxcZPHiwXHPNNVzz2i+WrWMBLjvASC1GFF555U2JiIh07EfF3gcfvFdVuifrQ0YMqrai0Et5FdGTk5NUO3yR/92McFoMERGR6/siV5ID+L7IdED/xRdfyCuvvKJGefv3768C9wYNGqiiaadOnZLjx4/L5s2b5dVXX5Vp06bJfffdJ9dfz2U+rCQ6OsZU+8jIKI+dC1WdnlutsymeemqCXHZZP8cauitWLC2RZcFAwdoQsGMlAlRtxXKES5YsKrU8C7IvcBzfMyXU+ngzQkREVPX7IhTAczUdMT8/P6Dvi0wF9GPHjpXk5GSZNGmSCubL6gH529/+pm4+Fy5cKHPnzpUffvhBZs2a5a5zpioKCwsz1b5mzXMBI1kPRm+1Cy9sUWrdcoz6Yf8vv+xV23o5O7IurKe6atVymTLlSYmPr1VqeRYc0+3I+ngzQkREVHm438HSdFjlx7kWTX5+vtqP+99AvS8yFdAPGjRIRowYUaG2CPaHDx8uV199tUrPJ+vQc6nNpNxzVNe6srOzHN8jaEfw0LJla6lTp46cOHFC9u3bo9KQjCn4UVHRPjpbqih0uqDz5VzRu+JHvc1OGXvhzQgREVHlV6DAOvNYug6r/KAwMAascH+7fPlPKpjH8UBdytdUQF/RYN4IN51MubeWatXM1UIsq9I2WUN4eESJbVSzR2C/Z88uVdMC28aUe+P8erImVDrHlIlx4x6QJUt+kG+++dIp5X6QTJ/+GpetsxHejBAREVUelmauX7+huvdxvi8aOHBwwAbzYDpSw4gfUrajo8+N8CENf968eZKUlCQXXnihGplnmrZ1ZWZmmG4fExPrsfOhqkGHC15vubm58thjk2TlymWybt1qVayyONW3h/Tu3VdeeGGy1KwZ5iiqRtauiI40+2bNLihzTWT0TuMDbeTIsRyttwnejBDZg6tCpETkewjay7ovCmRBZt7cJk+eLB9//LEqeIdieIDl6kaPHi1ZWVkSExMjqampar78u+++K02aBG5PiV3mXFcE17m2/vXE/CGYM+dtmTz5Rbn11pFy6lS6Wtcagf2kSY+q4/n5ZzmH3oYV0fWayEasiG5PvBkhsq7ff/9Njf45FyIN9NE/IqtxdV8UyCoc0GMe/CeffCJ33323dO7c2bF/6tSpEhUVJV9++aXUq1dPDh48qNpg/8yZMz113lQFrgJ0FE2Ljo6V06fTZf/+fSWOVa9eg8+3xQNABPStW7eVXbt+lrvvvsNlO32cS2JZGyuiBwbejBBZy9q1q9T8XHSEo5J2fHy8GqTCSjEoxoX5uciyISKyZUCfkZEh33//vVx++eVy3XXXqeDh6NGjcvLkSdm+fbvcf//9KkjEPqT+/vWvf1Wj+MeOHVPBfmQk5+xaSUpKSqnCW85BvN4PKDhhnGJB1gwAc3Jyym2H44G6PqedsCI6EZH3R+YRzLdt20EiIiJk4cKvHCP0Xbp0V1moOI75uxypJyJbBvQ//vijCtyRUv/oo8Wpu3o+PQK/1atXqy9jBwDm8z7yyCOqkB7m1JN1hIaGnDed3rjf7DJ35P0AsFmz5qrqp942TqvQ24cOHZCLL27FuUY2wIroRETegzT7sLBw2bFjqypI6rxUaFpaqipAi3aYv0tEZLuA/pprrpH169fL4cOH5cMPP3QEfLfeeqsaudX7tBdffFHS09NL7SdrMFvlnAG99R07drTMGgnGbWM7si5WRCci8g58RqKQLLJPe/bsXWqNa6TfY41rpN2jHQuREpFt59DfeOONctNNN6mvLl26yJYtW2TTpk3y5ptvOtosW7ZMvv76a/V1zz33eOqcqYqQTmYGKqOTdeEm5PTpUy6nTBinTgDa4eaFVXutjxXRiYi8U4fm7NmzanqoczAP2Mb+7du3SGZmJuvQEJF9A/oOHTqo4P3111+X9957T+rWrStPP/20XHHFFY422L9x40Y1cs+A3rq4Dr1/L0MYGhqqgny9bB1uRvLy8kq0j46O8cGZklmsiE5E5Fk1ahTfCjdq1KRUMK9hP47v3r1TgoODeUmIyL7r0KMoHr7K8uyzz6p59iyCZ20pKcmm2qMoXv36DTx2PlQ1xvU3kS6IdECMwutl63D83XffUemCxpsXsh+ddUFERO5RUFC87Ovhw7+rznAE787r0GP/4cO/qXYYzUfHORGRVZi6s1+zZo307NmzzOMNGrgO+lAwr1evXubPjjwiMjLKVHuO5lobRuK1li1by8SJD0lS0gnHvsTEOqrAjw7osRY92QPXRCYi8iwE7Qjis7IyZdq019S0xI0b1zlVuc9Ule7RjivFEJGtA/qXXnpJ6tevL+PGjZNWrVqdtz3S72fNmiVJSUkyb968qpwnuRGWFjSjrBQ0sgZj+h8K9zjPoUdwr/cXt+eydXZbE9m54jLXRCYicg+MwKNmyYYN62Tbts1qu0WLlpKYWFeSko6r92KM2IeG1pSuXbszS4qILMdUpPbJJ5/IjBkz5C9/+YsajR80aJC0b99eGjZsKOHh4XL69Gm19jyK5a1YsUJVxf/b3/4m06ZN89z/gEw7e7Y4vayimOJrba46XOLja0lCQqKaLpGScrLEMRbEs8+ayN279yqz4jLXRCYico927TrIypXLJCoqShUC3rNnl/oCfJbm5uaoJZnRjojI1gE9birvvfdeFdDPnTtXvvjiC3nnnXdKBHwYFcQo/pVXXqmC+Tp16njivKkKfvvtkKn2v/56UK1fTtaEUQNnCOKdA/lz7Tn3z+qw1jFG5suruLx3726uiUxE5AY7dmxTn6UI2pFaj+lreoR+3749jhF6tOvWreypp0REvlCpXOrExER59NFH1deBAwfkjz/+UG+CcXFxKphv1qyZ+8+U3CYsrKZH160n73Jed/58WFjN+tdz/fo1Ks2+vIrLffr0l2+++ZJrIhMRVfE9F2n1qEfTocMljjn0GKHHfHmk4yPIx7J1aMd16InIaqo8Obp58+bqi+zD7LryXKLFXsvWVaQ9Cx1aFyoroxgT5syXB2mgaIcvZl0QEVX+PRdV7FEwePz4B1SH6ahRd6n9ISGhKgsVxx944G6uQ09EllTd1ydA3hcRYa7KPUforc25wwXBnZ4Gg0fnYI9F8awN1wejQiiAVx7UR0A7VlwmInLHOvSNHVlRqDWDFHv9WarXoS9+j+Y69ERkLQzoA1BRUWGl1mgl68+hv/rqEY4K98b0euw/155z6K0MN5KYo4lq9hgVcgX7cRztWLSSiMgd69D/Vu57rnEdeiIiK2FAH4DM9i5zRNfakBaoffnl55Kbm6sK+vTtO0A9Yhv7NaRok7UNHDhY0tPTVDV75xtMbGM/jqMdERFVHu5xcF+EefLlvefiONoxK4qIrIYLjAcgs8uWcQTQntdXj9Jj22zhPPKtxo2byJ133q2WpkM1exTA08sQYmQewTyOox0REVUePiOxROjWrZtV0Tu85152WT+Ji4uXtLRUWbFiqXrE9MOOHS/hPRER+V9Aj0Bh3759kpSUJJdcconqyYyNjXXP2ZFHFBYWB3oVpQNDsseydXhNGtfQLd2eKfd2gMrK9es3VEvToZo9MiswMoQ0e4zMM5gnInIPvKeuWbNSLrywhaSlpcn8+Z85jqFAKfYfOPALs6KIyP8C+i+//FJeeeUVFcyjh/PTTz+VN998U6UkYT/TkqwpJyfbVPu8vFwJDw/32PlQ1XDZOv+FoB3VlrHuvLHiMhERufe9tl+/y2Xx4h/U/azzOvQoUnr55YPYkUpE/jWHfuHChWod+h49eshrr73mCCoGDhwoy5Ytk7feesud50luhLVWzSirSAxZQ3Z2lqn2WVmZHjsX8gznistEROQ+v//+myxdulg6dOgkPXv2loMH98vy5UvUI7axH8fRjojIb0bo3377bbnxxhvl6aefLhEgjhgxQlJTU+WTTz6Rv//97+46T3IjzAvzZHvyrvDwiFL7dKV7Y8V7jcsQEhERnYOpTbGxcTJ+/D/UEnUjR44ttQ79Y489oNoha4qIyC9G6A8dOqRG413p0KGDnDhR/hrK5DtmB/nMjuiT74octmnTTnr1ukxq1KihtvGIbezXOMpLRERUDBmm69evUcVHy1uHHsfRjnWFiMhvAvpatWrJgQMHXB7DfhwnazK7DB1rIdinJsKRI3+omxN9E4JHbB85ctjRBsvYERERUfHSryg6iuJ35cFKI2jHpV+JyG8C+iFDhsgbb7wh3333nePNDcHDzz//rObPX3XVVe48TyIqQ15enmMEAcuZYdmds2fPqn14xHZ6erpj5OHMmeL2REREgQ6DHBi4QOG78mDZULTjIAcR+c0cesyPx3J1eNQpv7feeqtkZ2dLly5d5P7773fneZIbZWScNtUe1zQiovQ8bbIGvQzd+YoX6uOYE0hEvoXMGYwMIpgwTpshIu/C6w/LgS5f/pMMGTLM0fnt/PmJ42jHaWtE5DcBPXooZ8+eLatWrZI1a9bIqVOnJCoqSrp16yZ9+/blG56FnT59ylT7U6fSGdBbWFhYeKkihr1791WBPkbvV65cJmlpqY7jNWuWXLeeiLwHVbJRWAtzcZHdhs9SBAlYBxtLZxGR79ahnzt3plomFEG+7nBD5xv2IwMO7YiI/Goderj00kvVF9lHXJy5+ga1ayd47FzI/dABs2DBPMc2R/+IrAHTX2bPnqGqaQ8derWas4s0X4z8IZi48867pUcPfp4SeRs60/D6mzXrLdm0ab0akUdBYBSWxYg9pq+NHn0PO92IyL8C+mnTpp23zfjx4yv768mDzM6hRtE1zhmzrry8kkXuMJpQ3jZG7TlKT+T9kXkE892791IjgMa0XqT5YgQQx+vXb8iggcjHdCV7VrQnooAN6CMjIyUxMZEBvUWdOVNcMK2iuGydtTkH7BiRN+5z3uYNCpHv1rl2DuYB29i/d+9urnNN5MMOtwsvbCFpaWmOAnn47IyOjpW4uDh2uBGRZVW6Es+ePXtKfW3evFlmzpwp0dHR8uSTT7r3TMltCgrKL57m7HzF1si3jCn1jz02Sa07r5cmRGYFtrFfY0EfIt+vc+2M61wT+bbDLSgoWPbt2yMpKcnSqlUbGTBgoHrENvbjONoREfndHHqj8PBw6dOnj4wbN07++c9/yrx55+bxknWEh0d4tD15V40a517GCxd+JZGRURiHd4zGI5jAfi04OJiXiMji61zr1SuIyLPwGYn6Fhi8wGtw8uQXS0xLy83NlUmTHlXL1qHdyJFj2TFORP4b0Gv169eXAwcOeOJXkxsUFZVM0Xb3iD55V25ujuP77du3qhuNli1bS7169eXYsaOq2JYxzT47O0uioqJ5mWyES5zZG9e5JrJ2hxuCeXx2OgfzgG3sv+eekaodO9yIyK8DegQNx48fV8vZNWjQwJ2/mtwIVVvNQJoZWZdzBgWCB8zF3b17p0rHx7axEGJERKQPzpIqg0uc+Qeuc01kXdWqFU9bq1WrdpkFY7Efx0+eTC5z2gwRka9U+l2pZcuWZaYcIbBHyj1Zk9miaByhtzbcXOBmA2mBkJ9/1lEED4/Y1mrWDOMydjZc4gxV0LHcZFpaiqxYsZRLnPnBOtfGoACjflznmsi3WW4ZGRnqtegqYMf+jIzT6ntmuRGR3wT0mCfvKqBHhft+/fpJ06ZNq3pu5CEhIebmZoaFhfNaWD4d+2yFlq1DaiE6dFgYzx4Vl9u2ba8yKlADAWmeKHLYpUt3ycrKZMVlm65zjeuKDBoUyMN8XczLxTr06elp6jjaEZH3s9ywBGx5HW5Y8hWY5UZEfhPQ33vvve49E/Ia3ctcUadOpUvt2gkeOx+qGgTpzksL4nrVro30wJMqRVBDO87/sz5UUkZH2s8/b1cj9EOHXq0KqmEpJR384TjajRp1l69PlyqoR49L1TrzuG7ffPOlo5OmW7eeagSfwTyR9yF4T0ys4yh656rDLS0tVXWE433YuLIMEZHtAvr58+eb+uXDhw83ez7kBWbnxIeGup5TRtaAOfK40cDI+0UXXaw6YJKSTjgCedyoxMTEyi+/7FXtEECQ9Ssuo/OlZ8/epUaLkH6P0SKkb7Pisv0gaEcnDK4rOuOQMcWMGSLfGjHiLzJjxhuqA7VFi5YlOtw6d+4me/bsVOvTjxhxAy8VEdk7oH/ssccq3BY3KAzorSkv71xV9IrIycmWqCgshUZWpdPob7jhr7Js2WIVzCMwxEgCbk769r1cnnvuKdP1E8h3FZex/KBzMA/Yxv7t27dIZmYmMy5sCq9NdpYSWQOyZLDW/OLFP8i6davV5yY6w9E5jm18nl5++SDVjojI1gH94sWLPXcmZNkReq5bbm2Y9wcI1qdOnaQCBWNRvNWrV8jKlcsM7fPKrORLvlejRvHbcqNGjcuspoz9jRo1USsZ8PVpT1yKkMhabrnlDhXIf/75J7Jnzy71BYmJddXIPIN5IvKLgN7MUnQYOSJr4rJ1/h8oYA69Hl0wzqEn69OrShw+/Fu5FZdxHFAQMTTUXKFL8h0uRUhkXQja8YX3WFSzR6YU58wTkd8WxcPcovfff1/Wr1+vvtepvHjMzs6W/fv3y7Zt29x5ruQmp0+nm2qPAlxMubcuY9ou5v+1bNlaNm/eoAJ5zP9DIS6MNOA6Frdn8Gf1mggYdc/Kyiq34jKOox1rIthzKULnQoeoiYAq93i9EpFv4T03OjqGl4GI/DugxzrzH330kbRo0UJSU1NVkBAfHy/79u1TI0bjx49375mS21SrZq5Ca1lpv2Q9DRs2VqMJuuo9HrHdsGEjR0BP1obr1b17L9m6dXO5FZexdFLHjpewoJrNliLEtS2r0CGOowo+q90TERFRRVU6Uvvhhx/kjjvukEcffVTefvtt2b17t/zrX/+SEydOyC233FJqLWyyjpo1w0y154iutaFoofbzzyWzYhDQYw69UW5uroSFmfsbIO/CEmYYsW3XrqNERESUqLis16HHknZoR/aApeowMl9eoUN03nApQiIiIjKj0otpYlS+T58+6nuM0u/YsUN9X6dOHRkzZowsXLiwsr+aPMzsfDAuqWRtyIgx1/6Mx86F3AMjtEi/RgcNgjyM4CLgwyO2EczjOEdy7QEd3OvXr1GZFuUVOsRxtONqFEREROTxEXrMqcaIETRp0kSOHTumCuFFRkZK06ZN1TZZk9kUehaEsTYU7THSa9KXte3cnqwJc6mRfo0R24ULv3KM0KNgE0bmGczbBzrRcP0wZ748mFaBdvhiZhSR73AVCiIKiIC+S5cu8uGHH0q3bt1UQI8U3h9//FGtPb9lyxYV2JM1mQ3oGABam3OHC4I+jNrrdehROA1L1WnMuLAfY9FRsmehQ7wuUQCvPKiRgHYsdEjkG1yFgogCKqAfN26cmiuP9HoE9jfffLM8+eST8sEHH8jevXvlpptucu+ZktuYTbnGaBHnXNtjDj0geEele6ydm5R03LGWrsY59PariP6nPw1nRXQbQ8caMitQ0BDTJspaihDH0Y6dbkS+fc/F6xSFnjG9dMWKpVyFgoj8J6B/88035brrrpN69epJy5Yt5dtvv1VV7eHBBx9Uo/KbN2+WAQMGqECf/GfONQN66zKOvmsI4p0Dee3MmTxeT5tVREdAiNchRnpZEd3ehQ7LW4oQK1Gw0CGR795z27bt4ChEinslZLh17dpDLRPKVSiIyC8C+nfeeUdmzJghPXv2VIH9FVdcIZdeWrxmLkYU7rrrLk+dJ7lRSIi5dcjDwsL5/FsYbjjMtQ/x2LmQeyuiX3HFlfL++7NVoTTjHHrsZ0V0exY6RFDgailCBPMsdEjku/dc3Ots375Fvc/qlZrwuGnTevX+i6VCuQoFEdk+oF+2bJl89dVXMn/+fHnggQckNjZWrr76ahXcX3TRRZ47S3KrU6fSHd+Hh0eo3mjcVGq4yURvdHZ2ltrGjSb2kT3m0MfH15Levfuq65qdna3SBVNTUxzHmc5rj4ro7dt3kqlTn1KB/dChV5dKue/UqYtqN3LkWF5TGxY6NC5FyEKHRL59z123bnW52YuoX5KZmaHa8T2XiGwd0NeqVUutPY8vrDuPwP7rr79W8+bbtWsn119/vQwZMkQFEmRdxrpaCNqd52CfPJlcovgWq9xbm/P1OX36tAoWsAZ9jRo1pFq1kscZ0NujIvqmTRukZ89LS6Vn65T7NWtWSVFRISui23CkftSou9R1xbVGxhRfk0S+g9ehMZjHSHzfvgMcnajLli1xTG1DO65CQUR+sw59q1atZMKECbJ8+XJ566231Lz6KVOmSO/evdX+TZs2ufdMyY2KU8k058rZztsIDMm6nFPo8/PPOq4ZHrFtxAra1r+e6KQJC6tZKpgHbGN/zZo1VTteT3vjygVEvlWjRlCJLJoXX3xddZy2adNWPWIb+ys7zY2IyLJV7jWMAPbv3199ZWRkyOLFi+Xtt99Wo/cYxSfriYqKNtWey9b536oFCAbJ2rhCnX/islhE1v0Mbdu2vUyc+JAkJZ1bYjIxsY4MG3atqoIP/AwlIr8ZoXeG4B0F86ZNmya//vqrWqe+MvBG+ac//UnWrVvn2Pfss8/KxRdfXOLro48+chxH2j8K9HXo0EEtp4dlRoyjHy+//LL06NFDunXrJv/85z8dxU4CFdLJzGCFeyLv3lziPSo3N0el1qMCOrbz8nLVo66IjuPYxnsm2QMCgsmTJ8ru3TtVXYQxY8arR2xjvw4YiMh7jPeEKFqJaYetWrWRAQMGqkdsY7/GrBoi8qsR+j/++EMF0wsWLJCDBw9KQkKCXHPNNXLttddKkyZNTP8+zFHC8ne//PJLif0HDhxQ+/G7NSyRB9u3b5eJEyfKM888o5bSmzp1qkr5R0V+mDt3rjpHdDTgRvjhhx9WtQBGjRolgcpshwY+vDjH0z4p90jDNl5j522maFv/euIaoSgeAjxUWMZ7l66JgJR7zOPs3LmboyIz2W8pQld1EbgsFpHv69DExMTKxRe3kri4eImOjpHjx49JWtq5gSLeDxGR7QP6tLQ0tf48gvitW7eqG0ysO//II4/IZZddVukCavv371dBu6ueTwT0CMDRYeAMI/WDBw+W4cOHq22MwCP9//Dhw9KoUSNVsO++++5zZAw89NBD8q9//SugA/rTp0+Zap+RcVp9wJE1FRTkl9jG/D4EfAji8XrEtnGtehwLDTW3dCF5D64Zqp5v3bq53HZ79uxS7Xhzaa+lCMuri8ClCIm8LzT03BS05s0vUvc88+d/ViLlvnnzC+XAgf3/a8/PTyKycUCPdeZXrlypRouwTN2jjz4qw4YNk/j4+CqfyPr166V79+5qObyOHTs69mdmZsqJEyekadOmLn9u27ZtMnr0aMc2ivPVr19f7cfI1bFjx6Rr166O4507d5YjR45IUlKSJCYG5lJsZlN0WRTPPgV99FKEWOMatRJwY4JlzowBPQv6WF+7dh1k5cplarnIyZNfVAEfVqTAdBl0yEya9KhaahLtyD5LESK93jmY17Afr1usUMFlsYi8+/rUDhz4RXWStmzZWhIT60pS0nHV0WacU8+sRSKydUC/ceNGlU6Pdefbt2/v1hO5+eabXe7H6DzeXFFoDxX1Y2Nj1bJ5Ov3eVWCOlPrjx49LcnKy2jYer127tnrE8YoG9NWrV1Nf/qKoyFzV+sLCAgkKclu5BXKz/PxzNyNYou7UqXT58svPS4z4Yj+WONPXv6yggqzh55+3SVRUlJq7+fe/31Uq5R6dcihWuXPndunV61z1ZbKm3NzipQjr1q1b7ntpnTp1VLvCwnyOAhJ5SVZWToltDAb98stelQWF91xsGzvFc3OzJTraXHFh8q2goGqOR97Pkj8ydVe/atUqr99kYG4+AvoLLrhAbrnlFtmwYYM8+eSTag79wIEDJTc3t9QcUmzjpgjH9LbxmNlR6vj4CL9Ka83LizPVPjExVuLiIjx2PlQ1+fnnXpMI2pE+iFFcHQBiRF6/FvT1rOzUGPLWaO5aNU1ozZo1pd57sI2vDh3ay7p1a+Thhx/0q/cnf1RYGKY+O0+fTi33vTQjI021q1MnjteUyEuiooo/Q/F5ifffst5z8bmJz9VGjeoE9GcoBtJOnz4tdpKeftLxmJISJnaDDiQ7ZhVj8BSZ1nYUGRmpOuH9MqD3xbwhzI3HnHiMzAMK36GK/n/+8x8V0OOcnINzbKMyuzF41+eu25qp3J6amuVXI/RZWSXXJT+f7Ox8qV49y2PnQ1VjDNZx04GU+759z6XcL1tWnHKv61MkJaVz9M/i1xPXC8F8r169ZdSosermUb+P4YZyzpx3ZPXqlerm88SJ4iCQrK1btx7y/fc/yBVXDFFZFnqFAnxO4foiC+O7776X7t17Snp6tq9PlyjgUu7x+OSTk2Xp0sWyZs0q9V5bXNOkh/Trd7lMmTJJtcPrM1A7UU+ePCmPPPKA6eVyreKVV14RuxbL/ec/X3NkGdsB7j/HjRtj21UhqlevLtOmvWN6qW9PqMigquXzbvGmqYN5DaP1a9eudaQo4g3GCNsooIdjgNT7hg0bOr4HVwX2ylJYWKS+/IXZntVTp05LzZrhHjsfqprq1YPU6wRvmhde2EKl3M+bV7KgD/YjhbB4lCGoRJo+WQuuDz5IatasKbffjvogCPYKpaCgUM6eLb7BxP5Nmzaqpex4Pe3hiisGq06Y119/WdVC2LhxnSOg79Klu2RlZUp6eppcfvlVfH0SeRHeRwGfoTNmvKnqluA9FkFrSEio6mBF3RIdmGRn5wZsJ2p6+in1vARf0Euqh8X4+nQCQmHOKTl7cLV67mNjq16zzFvCwiLlhRdek+xsz3RQHzt2RGbOnC5jxoyTevUauP33h4eHq/+DXe6XLR/QoyL9li1b5L333nPs27NnjwrqAWvPb9q0Sc3tBxTBwxf2I6BHgTwc1wE9vsc+O6au+HLZOrI2nQ6IoB2PxoI++/btUQV9kE7Ia2kfeNkdPvy7LFnygyqopoM/VLYfMGCQr0+PTGrcuIka5Vu8+Af1GsWyWPXq1Zdjx46q5Qnxvnz55YNUOyLy/lKhDRo0kkOHDsi4caOkRYuWqjMcn534DMXrs1mz5nLkyGEuFYpu5rAYqR5hn+CSfAOvIU9DMN+0aTMJdJYP6JFuP3PmTJkzZ45KsUeV/fnz56vl6OCmm26SW2+9VVXGb9eunVqHvl+/fmrJOn385ZdfdsyDQLrNyJEjJZDVrGlu/lCg9kTbBXrLdScN1s1FoLB58wZV0EcHgKjSq9fRNU5BIetez9zcHJky5Ql1TVEdPSGhjiQnn5Bly5bIqlXLVVt00PB62mcdeqTyduhwiURERKgR+t27d6rXaI8el0pWVpY63qfPAAb1RD5YKhSvxxEj/iLffPOV+vzEl75nGjp0mHp9cqlQIrIiywf0qKaPUfo33nhDPTZo0EAF5Z06dVLH8Th58mR1/NSpU3LppZfKlClTHD+P9eZTUlJk/PjxaoQSFfr/9re/SSBzrh+g07XL2jau0UrWHF3ADQnm5SLdHqP0Q4YMU4EggvgVK5aq/QgcME/XuYgkWe96opAhChvqeZp4PSLQN74u8T3a8Xraax368eMfUK/VUaPucqT04jrjtfnYYw+odjhGRN4zcOBg1VH6xRefSHx8LRk0aLCqR4PlQvV+3Y6IyNYBPQrSVbQQCNrt2lXcu2nW3r17S2xfccUV6qssSLfXKffOEMRPmDBBfZFrzmnYTMu273r0jz32lErRXrjwq1Ip2i+9NFUFDWRt6JxBZwyWrMN65F99NU/mzzfWRKirAr53331H4uJqBWxxJruvQ4/rbOws5Tr0RL6F91K8VjMyMmTBgnmO9ebRyYrvA7myPRH5UUA/btw43jz6AVRuNSM/31xVfPJdijbWn0c6r+6UwSOOffnlZ+o4U7StD9crNTVFXavZs2eoEVx0TOplCFE4Dftxo5maetJx00nWfo2igw3TJsqTkJCo2nEaBZF3ITMGI/KZmRly5sy5NeeLPzOLt3GcGTREZPuA/t577/XcmZDXREZGebQ9+aagT8OGjWTbts1qFAEFfVAU8sSJE46CWxdc0Fz++IMFfewQ/BkzKdChZiyghnoI+kYT7Rj82ec1ihoI5UlOTlLtOI2CyHvw+YjPSf2+e+4ztK6cOFFcWBZtEOyjHTKn2IlKRH4zhx7BAqrGG9eBx5teTk6ObNy4UV577TV3nCO5GVI7kZ5dUHD+9Gu0Y5qZteH6tG7dTrZu3SQXXXSxmi9vLOiDKqMxMbFqbn2nTp15I2KD4E/XsWjfvqPqUHMuoIYby+3bt6p2DP7sU3Rr+fKfVH0LnXZvhGACx1l0i8h3najIksGydXhfVcuzBYeoe1wsW4cON3aiEpFfBfTfffedPPTQQ+rNzVi4SX+vl5Uj60GnS0WCeUA7pvTaB4L20ina6WrpHeAKhPagX3N//vO1smzZ4hJTKBAcYv+OHdtY78JGUExrzZqVMnfuTLnjjjFqHwpuIY0XsB/TKVh0i8i7MHChjRkzXv797/dKLRWK/VOnTlJtUIyUiMgvAvq3335b2rRpI0899ZT8+9//VsHD6NGjZdmyZfLqq6/K448/7t4zJbfJyckutU+PCDpXuIfc3NxSlfHJWh00O3duL5GiXbyG7rl16DW0YweNteXl5apHXCfcQOKGUi9LqIurrVy5zNA+T2rW5EoUVof15e+8826ZOXO6YxqMhk4aXO8xY8ZxyToiH73nVqtWXZ5//ulSS4Uic2b16hXqeFFRoXrP5T0REVlJpUt2Hjp0SAXwrVu3lu7du8uePXukefPmao332267TQX8ZE34MAIE71hzFcGAcQQQ29ivsy2MBWLIepAWiCXOACn3tWolqHT75cuXqEdsY39x27MlpsiQ9SELCh00/fsPVI9cqcC+9u/f5yhUaYRt7MdxIvIu/fmJYL1Wrdry7LMvyZ/+NFwuuaSzesQ29uN4cXt+hhKRn4zQY0QhJiZGfd+kSRM5ePCguinB/j59+si8efPceZ7kRjpdDDeQ8+Z9qradR+ixXwf5mENG1k8XRHr9gQO/qNGFq68eIVFRMZKRcUqN5mK/TsNnuqC1GZcya9u2g3qf3bBhrWMOfc+eveXUqVPy88/b/tc+1IdnSxWFzIrFi39Q32Od6z59+qtlB9PSUtQIIFY2wHF02iDFl4i8w1j4F8uF/v3vd6mOUz1tDTUvjB3hLBRMRH4T0GOO/ObNm6Vr167qe7zZYZQeI/anT5/mKKCFGQsyoRMGvdPGEXpsO6eDknXp0QLcfOgiat9+u8Ax/69Ll+6OImqA/UzRtofw8HD5299Gqy/Mt46IiFSv0Vmz3vL1qZFJH3/8b/XYvXsvlXpvfB9Gei+WIly3brVqx4CeyHuM9zjGeyFXj8AK90TkNwH9jTfeqObPZ2dnywMPPCA9evSQCRMmyHXXXScfffSRml9P1h8BBFfpnyXbcwTQLlAoDaN/qKStR/9WrFiqRv/IXvM59aguVi9AZ40eLcKXcbSIc+itD6N9eA0iO0YH89ini+JhG/s3bdqg2ulsNyLyPOcUerzX6qAdj9g24lKhROQ3Af3111+v3tT++OMPtT1lyhQ1p37q1KnSoEEDFsUj8hLjlAiMImRkZMiXX37umEKB48bRBS5zZg9YPgnLJBmDdx3YG4+T9SFDBho2bCybN2+Qzz//2LHyhF5aEnVLGjVqJIcOHVTto6OLp7QRkWfhM1J3oKEzzVinxBjMoyge4nx+hhKRX61D/9e//tXxPW5Evv32W0lLS5P4+PhSPZpkzRHAirVnFW0rc16C0FjEEIG8c1FDTKlg1oW1M2jQEXO+YB3H0Y7X0vp03YoTJ47LjBlvqOChVas2Uq9efTl27Kjs3btb7ddL2LFuCZF34bMSXygge+rUuaVedYdbTEysWhZWpHjknojILwL6yy+/XKZPny4tW7Z07MPNJYL57du3q9H6devWues8yY3MVsl2TsEn666hWxEsimdtCPYQ2GVlZTqCO3Ta6DRsXG+dIop2nM9pfWFh4eoRKfa6iraxjgWWBn3iiYclJeWk2maNCyLvwfupzmLD6/ORR55Q77cI7FFkFubMeVsF9MWd5GfYkUpElmIqEvj6668dweCRI0fkhx9+UIXwnK1Zs8axDAhZj9lrUxw8FN+QkvVH6MF51QIjjtBbG24kdTCvr+/FF7cqMZqroZ2+zmRd6IgJCgqW/Pzzv/eiHa+n/RQXmD1TIn2b7NUpXr9+Q1W3ZMuWjaWq3ONzE8ePHv2DneJEZO+AfseOHfL++++r73HD8dZbZVdavuOOO6p+duQR+IAyAzeYZI8R+oiICDVqq9O1EexhrjVGBrOystQ+jtBbW05Odolt3Ezu27dHLVvnagkljO6GhYX54EypohAc6GAeo/Djxo1SnTR169aT48ePqU4anQmFdiyKZx+///6bLFr0rQoE9coiWKVg4MDB0rhxE1+fHpnoFE9NPenoANfTRvGI91zs1xk07BQnIlsH9A8++KDcdttt6o3tiiuukGnTpkmrVq1KtMENZ2RkpPoia8KceDMwBxuBIlm/JgKCdnwZR+id52Lj+jMAtP7rE9fuySeflSVLfpA1a1Y6jiNYGDBgkEyZ8oSjRgKvp7WhQw1at24nu3f/rL5HBw2+ACO6uN6YV79r188q8yIqKtqn50znt3btKrXcYGxsnFp6MCGhjiQnn5Dly39Sr1msXNCjx6V8Ki0OWRUI2nXnaG5uyXukM2fOqmkwOTk5qh2L4hGRrQN6vImhgj0sXrxYEhMTOdoXEAF9ySVdyNrXE8GBHu1DwGfcBgaA1mbMoDh+/KganTeOFmG7deu2Llc5IGvSxe6Kigrl6aefVyO6WHMeI3243libHiO6//3vh6pdRAQ7xO0wMo9gHtfujjvGqEBPw7Khc+fOVMeRps2RemvDZySWe0UhPATtzvC61fvj42tzSgwR+U9RPAT2hw4dkjfeeEPWr18vp0+flri4OOnSpYvcc889cuGFF7r3TMltzKZcM0Xb2pyrnCOIb9mytdSuXVtOnjxZYs41hISUbE/WogMDXMeZM6erm01czzp16qoq6QjosV/jfF17XFNUysZrEY+jRt0lt99+pxq5R/COzDaMDhYfr8tragPolMHIvHMwD9jGflxPtMP1JutCh7exqj0Gr/QSoXht4ksPbCQlHWfdEiLyn4B+//79cuONN6o3ugEDBqjgITk5WX766SdZunSpfPrpp9K8eXP3ni25hdkAgAWarL/MmYapEWFhEbJnzy7Hvtq1i+fQ67RfLnNmn+sJ1avXUNWVcU3xfottY8YFr6c9YJ15LE33+OMPqvnzWI9ez7m+5JKusnfvLnVdR4y4wdenSueB64Q580izdw7mNezv06e/fPPNlzJy5Fh+jlqYXjVEi4yMUtcOFe7T0lLVFIrU1BTHcVa5JyK/CehffvlladiwoXz44YcSFRXl2J+RkSG33367vPbaa2qOPVmP2WXonKukk3VvRlzNoT95suQcetyMcFksa3e4IYsCUyPAWBm9OPW+OP0e0I4dbvaA2gcIDHbu3KHmXteunSC1aiVISkqy2oY2bdqpdmT991y8j2LOfHlQkBTtGABaW0HBuXuiSZOmqrolCxd+VaLIIeqWTJ48UbVhVhQR+U1Av2HDBpk6dWqJYB6wPWbMGHnqqafccX7kAYWF5wICT6xbT77voNGdMK46Y9hBY214velg/nzQjhXR7TPnGlkWTZo0VVMnTp5MVl+ADjZMqcBxtOOca2tD3QoEeiiAVx4UJEU7FlGzNnSqATpHGzVqrKZIYMoEOm50pynel3VHOa5r/frF9aSIiKyg0oulIp2srFRPfHixkJp1ma2ejPQzsi5OofAvempERRnXrCfrwlzqsLBwFbDrYpWAR2xjP46jHVkbrpnOuCirwxv7cRztmEVjbdHRseoRr0MUM8S1wzXG9CcdzGO/7gyPiSluT0Rk+4C+Xbt28n//93+lRvuw/e9//1vatj1XhZmsBTeNZjA929rMVjnnaJG11awZVuL7atVKvk1j29hGV1An60IWBaraZ2ZmlJkhg/04jnbMorE+rEqQnp7mCACNdACI42hH1mbMNF29eoU89tgD8tVXX6ilB/GIbezXwsPN3UMREVk25f7++++Xm266SYYNGyZXXXWVJCQkqKJ43333nap+P3fuXPeeKblNTk62qfaovswPMPsU9DkfzqG3toKCc8FBbm7xUkmYb41llVCYCWnaej9g6TMUyyNrv0ZxnTRd3wJ0Gu+5tmc559oGMC0C68xjaTpUs0cRNcyZRzo2RuYRzOM4p09YH0bjkUJ/9OgR9Xps1qy5Kmao59C3b99JvffidYp2zLggIlsH9JdffrlMnz5dWrZsqUboZ8+eLa+88ooqfqdvUDAyP2vWLOnatavnzpqqBEsMmoFRIwb0RN7hPNqHCug//7xNBfK6IjoqpFe2yCV5X40aQaWmPRUHgHXUPGwEgCkpJx3HuVSoPfTocalaZx7TJIwBINLsMTLPYN4+xo69V5566jF1L7tx4zp1z1OrVm05dSpdbRvbERHZOqA/cuRIibnxPXr0UMvT5eTkqCAxOjpawsLOpYKSNXEdev8OFlDEB6O859bQDSpRZI3BgrUVV7I/B8E7Ruh18GcM5p2r4JP1s2i6d++lRm6Ny50NGTJMjfQi3R6YRWMfCNpdFVEj78D68dnZ5rIOy3LttX+RefM+UUE9fqfx9+KaXnPNDaoD9ddfD1X530KHQWJi+askEBF5POXeCEE8A3n7wFrlRrgBQZpnUVGhSj0LCgouEQAa5+uS9RjTr5s3v0gyMk6rmxwdHGKUAXMEDxzY7yi6ZrYwInkPXo8arhtef0jj1RXRkdaLa44lQitTE4O8z5hFoYvhYR8CQF0DwxgEcg69/egiauQ9+KzD/HZvvF7wb3zxxcfqy11/L6+/PoOfxURknYCe7MU5AMBNpf5A1DeZRiyKZ58A8MCBX1Rg0LJla7UMFpbHwvxOHeADA0BrM1atR9COgG/YsGvViA5GjFauXOYI5uH06VOq04asD69NjMIjywJTK3QWDUbr0anqPJ+eiMqGjukXXnjNbSP0RkeP/iGzZr0lo0ffo6ZVuBvez9mxTkQ+C+j/8pe/VKgdbkx27dpVmXMiD0PPcHR0jAoEwNVKBRraMX3Q2pzXLEcA+Msve9Wa1ggWsG1sg6KIvJGwLudrg2JMqLRcFi6hZH16VB7vrfjKyzv3ekRQ7zzNgu+5RBXj6bR1BPNNmzbj5SAi/wroR4wYIXXr1vXM2ZBXYBS+omtXo52xIjNZj3HZsri4OGnZso1s2rTeMfrXuXNX2b17p6q6DBERkT48Wzofsy81XGfjfGyyHlep2MiqwBeK4RkL4hW3P5d1Q0RERFQe03eBN9xwg7Rv397sj5GFIKXeeUSoLGiHAk28wbT+6B+kpaWplN4WLVqqkQuk2mPbOIeXnTPWhowKXFN9zZzTsI3baIeq2mRtuE7oSNMdqdWqVS8RyGMbNUwgMjKSr1EiIiKqMA7rBCDcPAKKbRkLqjnTxzn6Z23Gmge6iBrS7fHlqogaO2isH/yhqr2ue4DgHSsVoPAoVhQxrlNfu3Yigz8bZkUheNcdM8WP5zrcMjOZFUVEREQVd25ojwKGDuLLC+aNx1EVnaw9ootR2gsuaK6CdlREN8I29uM42nFE1/rB37mR2+L8ewTxmZkZjmBe709JSWYRNRtA3QojvAb1NcSj82syNzfXq+dHREREARLQjx8/XurU4bqZ/jTnuiI459r6I7rduvWUpCQdyDtPwi7exnG0Y8q9fabE6NR6THlJTEx0TH3R+/WUGLI2VLAHZDtNmjRVvQ515hMesY39yMQobs9rSkRERB5IuUdAT0TW065dB7WcWTHnZa+KtzHCi3ZkjykxOvsCRQ2xzBk6ZDCS26PHpbJp0wZH0McpMfbpREX2RaNGjWXUqLvkr3/9m8qwwLQJdNRgGTudes9OVCIiIqoozqEPQHq5uorKyDjNpbEsbs2aVRVqt3btKjUaSNZlnApz8823ybffLnCMwuPx4MH9av/77892TInhMoTWpgN1BPSTJz8hSUnHSyxdV5yBUddRCBHBPVaoICIiIjofBvQByGyKbkUr4pNvIAjYunVThdpu2bKJyxBaXFBQsON7HbQboViecT+KIJK1IdMCmRQI1A8f/q3UcQT3ej/asc4FERERVRSL4gWgM2fyTLbnfE4ry8s7V0ArODhYunfv5QgI8Iht7D/X3tz1J+8yVkPXsF75hRe2UI9Vzbgh39S5aNiwUYXaoh3rXBAREZHHR+hHjRold955p/TsyfRdIl8ydrgUFBTK/v375Kqr/iQRERGSlZUlq1YtV/vPtWHGhZXFxMSW2mdcs9xZbGycF86Kqur3338vEeDr9HrnbWM7IiIiIo8F9Js3b+Yogh9VuccIbmRklCqcpisyazVr1vTi2ZFZqHFgHN07ceKYfPXVFyXm52L/77//qrZxjRHskzUhuHOVhh8ZGanWKM/PL/n65GiuPTrdCgvPdaQhrR7vs3odemzrjjm0Q6cb59ATERGRR1PuL7vsMvnqq69KBX9kfQjcneE6pqWluryertqTNQNABO3OKfXY1sE8MAC0NucU+lq1aqkgPj09TT1iu6wOHbKm5GS9pGSx4or2xatP4BHbRmVlYxARERG5bYQeo34I6L/99ltp3ry5hIeHlziOoOH999+v7K8nL1XRrghU0Y6OjvHY+VDVxMfXNtm+ZEBI1paSkqLmzuO6paamMNizcZX7ird3XnqSiIiIyM0j9MePH5dOnTpJ27ZtJSwsTN2AGL+M8wPJWszeLFavzuWTrKxaNXPtOYfe2oxV66+55nq1jRHbX37Zqx6xjf3lTaEha4mJKVnnwPnz0XmbyxASERGRx0foP/zww8r+KPmY2ar1GNHH/F2yJrODeZyba58q98uX/ySvvfaW+j4lJVmtVY4OmSeeeLhEir6r6vdkHej0doYsNj2H3rmTlXVLiIiIyGvr0J86dUo2btwoSUlJcuWVV0p6ero0a9aM83QtLC4u3qPtybtOnUo31R5zsWvXTvDY+ZD7qtxjRP7uu+8otz2r3Fvf2bOlO1GNc+hddboyqCciIiKPB/QzZsyQd955R3Jzc1UA3759e3n99dclLS1N3n33XYmOjq7KrycvjyBFRkZLZuZpyckxN8eefAsV0LWQkFA5c6b0OvPG/aGhXLXAykJCQlQwh/fV80H6PTMurM+56N35cMoaEREReXwO/UcffSRvvvmm3HHHHfLJJ584RhluueUWOXz4sPzrX/+q7K8mL1dcBgTxycknXAbzrLhsnyKHOmhHCvaFF7ZwpGIbg/ycnGwfnCWZcdll/SrYri+fWBtwXnnifFx1yhERERG5NaDHHPoxY8bI/fffL23atHHs79u3r/z973+XJUuWVPZXk8WK4rHisrUFB58boYdu3Xqopcz279+nHrFdXnuynuTkZLe2I2tNqejZs7cEB4c4MjKwbZxqQUREROTxlPujR49Kt27dXB674IIL5ORJrqNrVRER5qpiR0SwIJ6druf69WvVyDzmyZ88may2y6qiTtaDdOtt2zZXqC3a6cJqZF1Y5tVY82Lv3t0ydOgwVZ8kLS1VFT801sLAFBkiIiIijwb09erVky1btkivXr1KHfv555/VcbIm55v/zp27ydatm1T1bMzH7dixs2zatN5xvLCwwAdnSRWlR/qcp0mUNVUCI4JkXXl5uSWyYhAMnjlzVq1lXr16dZVhoVO40Q7fs4CateG6GWVkZMiCBfMc77nOS4Oyg4aIiIg8HtBfd911ag49biT79Sue75mdnS3ff/+9KpSHufVkTc4jtAjew8PDVbVsVEA3BvPAda7tM4e+IrKzs7jOtYU5F0RDxXMd4OOY87KTnBJjv4AeVe910I5risDeiAE9EREReTygHz16tPzxxx/y8ssvqy+47bbb1OOf//xnGTt2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lIdFDom8X6EY05h++ulH6dmzd5lz6HEc7TBqT0REZIk59O+9955af/61114rFcxDZGSkvPTSS9KyZUt5//333Xme5NOiW0zXtrLw8AhT7SMiIj12LlR12dnZlZpmQUTegQzFuLh4lRlz660jSwTzgG3sx/G4uFrMoCEiIusE9GvWrJGbb75ZatSoUfYvrF5dbrzxRlm9erU7zo88wFggzRPtybtyc3NMtc/OzvLYuVDVmb0+LEpK5P1pMampKapz/MMP3y01LQ3b2I/jqaknTXeiExEReSygT0pKkiZNmpy3XcOGDSU5uXLpvphrhvn369atc+zD/Py//e1v0rFjRxkyZIisXLmyxM+g8wA/06FDB7nttttUe+fMgssuu0w6deokjz/+uOTkmAuA/A/n2/oTVx0u2Id5na6PMf3TymJi4kqN9ulOVDw6jwa6cx1TIqrYHHoE7f37D5R161bLY489IF999YWaN49HbGN///5XqHa4ryEiIrJEQB8dHa2C+vNBm/h48+sZ5uXlyT/+8Q/55ZdfHPvQsz1u3DipXbu2fP7553L11VfL+PHj5ejRo+o4HnH82muvlc8++0z9u/fcc4+jR/z777+XadOmyeTJk9U0gG3btqlpAYHszJlck+15M2JloaE1XaZhp6enuUzHZnEmaysoKHnNEBDoaS94dB4NxFJZROQ96BTFvHhMPZw0aaq0atVGVbOfOXO6esQ29sfExKp2nENPRESWKYp3ySWXyPz589UoeXm++OIL1daM/fv3y4MPPlgqNW3t2rVqxP2///2vKs6GQntI/Udwf++998qnn34qbdu2VcvlwfPPPy+XXnqprF+/Xrp37y4ffPCB3H777dK/f391/JlnnpFRo0bJww8/bLo4nL9wXqf8fFhB29qcAzq9ZF1Z2+g4C9S/fTswWeReTXMiIu/Baw5L06GaPQrgjRp1lyqMh5H7kJBQ9Z6Ljrc33nhZteNnKBEReZKpO0EExitWrJC33nqrzDavvPKKCrjR1gwdgH/88ccl9mNEvXXr1iUqrXfu3Fm2bt3qON6lSxfHMQQqbdq0UccxmrVjx44Sx5G2j1HLPXv2SKCKiooy1T4y0lx78q6srJJzrp07xZy3zc65J+86ezbPVPvcXI7QE3kb1plHFhSq2SN4R5CPbCkdzGM/jqMdERGRZUboEUg/8MAD8uqr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uQficBZQ5YI6O5fRaL99//33dv3117sR6PD/0BQSCAr+UemuyrG1PlcX7Yugi/4Nf4OCNpVV2X2IlsUo5PM76h+ty9VgjPZFCNHGW+EBH/5ZtWqVO7ccftMeCFoSE75HiX4/69WrZ0FHoAfibG3R1KlTbciQIdamTRtLS0vLucA/Kidr3ry527RSx0uqzExVF9dee220m4YjoFCg2YXQpUKFCu6if8NPqrbQjO5dd93l3ljqd1Tr5wcPHhztpuEING7c2J1RruUS69atcwM2qampNmDAAPrTYxs2bOBUkTigAfCkpCT391aDbm+//babnb/88sst6Ci5B+LIW2+9ZQcOHHDriXQJt379+qi1C0dG6281QKMlFP369XMnUeg/riuuuIIuBWKAjjibNWuW3XfffdanTx83QNO/f38Cvcd0SoH+5irE62/upZdeSmDwnJY66RQg+C0lJcVtUDlhwgS76KKLXBWUzqTv16+fBV2pbG39CAAAAAAAvELJPQAAAAAAHiLQAwAAAADgIQI9AAAAAAAeItADAAAAAOAhAj0AAAAAAB4i0AMAAAAA4CECPQAAKBachAsAQMki0AMAAuPyyy+3E044wb744os8v37WWWfZqFGjSqQtehw9XqzJzMx0bWvdurWdfPLJtnTp0jxv17RpU/vLX/6S8/lbb71lI0eOtFj1/fffuzbPnz+/WO7v559/tgcffNC6detmLVu2tA4dOtiVV15pr776apHuV32qdgIAUBiJhboVAABx4sCBAzZ69GgX7MqUKRPt5sSc999/3xYsWGDDhw+3jh07ugGQwnjqqacsltWsWdOef/55O+aYY4p8X+vWrbPBgwdbYmKiXXHFFda8eXNLT093gxq33HKLvf766/bwww9bUlJSsbQdAID8EOgBAIGSkpJiGzZssClTptiIESOi3ZyYs2PHDvfxD3/4g9WvX9/ihQZvTjrppCLfz549e9xgR40aNWzOnDlWqVKlnK916dLFzjzzTPvjH/9ojRo1sptuuqnIjwcAQEEouQcABEqzZs2sV69eNnPmTFu9enWBtz24rDyvkmiVpw8aNMjN/irQqfy6f//+9u2339o777xj559/vrVq1cr69u1ra9euPeQx9H2dO3d236eS7S+//DLX1zdv3mw333yztW3b1t3PwbcJlZLPnj3blX/rNi+99FK+1Qlz5851bdLj6XE1k7xv376c5xJacqDnoiUKhaHbLV++3F3UlmXLluUMDtx9991upr9FixZ28cUX25IlSw7p42effdY9bps2bdzzvPfee23v3r32wAMPWPv27a1du3Z255135rRTPvzwQ3d/Whpwyimn2LBhw+zrr78udMm9Pqr64PPPP7d+/fq59imMz5o1q8Dnqu/74YcfbMyYMbnCfMg555xjPXr0cBULu3btyulXvW76Hi1j0Nf1Wuj5TJw40U499VT3PFQ5Ev4cQz755BO77LLL3Gur/tHSBpX8h7dJz2XevHnuvnSbr776qsDnAQCIDwR6AEDg3HHHHValShUXoPbv31/k+1u5cqU988wzLrgpoClYDh061P37mmuusUceecS2bNlit956a67v+/e//22PP/64m8nVbXbu3OnCsUK8KLRpcGDNmjX2pz/9ySZNmmRZWVl26aWXHhJeNdAwZMgQt65boS4vCtdqk8L6tGnT3P2o3Zpx1oZ2+qhgLGqXAmhh6HYKlLpogEIl6AqmCrEqQ1clhO7v6KOPdqXqB4f6hx56yM2g6zYabHn66afdR/WZBhzUJy+++KK7Xr777jvX1hNPPNE9jwkTJrgBFPW5+qewdFv1vQJ2amqqC9vqPy07yI++VrVq1QJn+3v27Olm8j/66KNcoVzPR5UhKssvXbq03XbbbfbCCy+4n5HJkye71//gpQsff/yxXXXVVVa2bFl3G/3sauBEpf4a9AjRAMGTTz7p+kI/18cee2yh+wEA4C9K7gEAgXPUUUfZPffc48JrcZTeayZWYSsUohS4nnvuORfOtFmabNy40c04//LLLzkzuwphenzNlotmYBW2FVw1C6uSbs1yawa7bt267jadOnVyAfTPf/6zPfbYYzlt6N69u/Xp0yffNmrGVqFYYVLBVxT8tbb89ttvt/fee8/OOOOMnDXmqmSoV69eoZ7/cccdZxUrVnT/DgVdBVWtNddHPa9Q2xXOFdLDqwj0/Xo9RLPLmmnOyMhwt9M69dNOO82tS//000/dbVatWuXCrIJwrVq13HUaLNDgwe7du3Pa8ltCgxiqnhBVCCxevNj++c9/2umnn57vTH/otchPqA81kx++2aCeo9opWvah5zR27FgbMGCAu06PqeqJ8Nl1DeKofP+JJ55wgwCi/tSggfpQgzIh1157rau6AAAEBzP0AIBA0g7zF1xwgSu91wx4UQcIwmdEq1ev7j6GgqxUrlzZfVSgD9Ea9VCYF63LViDWrKxoJlvBWqFVgVCXhIQEF4zDZ39FtyuIBhlEQTCcPldQDJXJFxe1Xc9Hs/WhtmsAQ2XtWuqg2egQlZuHqC2qntD3KcyH9582ngv1a3Jysl100UVuRlqz5scff7wbmClsmM/rsVUloNl3DQoUNAgQ3q68hIJ3+DF+an8ozIdm7CX8pAO9tueee27O55rl15IADbTovkL9qJ8b/bxp2cHh/AwAAOIPM/QAgMC66667XPBUiXJ+684LI78QWb58+QK/LxT8w1WrVs2VZotm5zWzr3CbFwW+wj5WKEArZIdTOFWADoXl4qK2p6Wl5dt2fU0DIfn1X0HPR5UDWiqgMnlVHfz1r391VQ+XXHKJK6EvVapUodupUvZwCtXhQfxgmp3Pay+Eg2fxpU6dOjnXVahQIc/XQ30fLvz10eCPlgXMmDHDXQ6mQY1wv/UzAACIPwR6AEBgKVCq5Pm6666zqVOn5nkbzSqHK2j29nCFz1KHB13NEod25FcJukri83I4x+6FwrPuP7xkXKXt27dvPyRYFpXa3rBhQ1c2n5fClvPnR5UNWnOvPRBWrFjh1u5Pnz7dzdRr+UGkaEb93XffdeX/WnOfl9dee80NFOS3l4GE+vvHH3/MFfxDpwyEBgE0OKE19AdXVki5cuWK+GwAAL6j5B4AEGhas37eeee52d7wncNDM8dbt27NdV1oHXdx0EZumzZtyvlcM/PaYE+7uovCvG6jNdTahT10efnll93MdKi0uzB0X7Jo0aJc1+tzDVpo/XhRaGb74MfT81HFQXjbVSauZQ6H0/aDaW8Cle4rzGtQQ/sUjB8/3n0ttKFgpGiZRoMGDdwGgxoIOZhONli4cKHbK6Cg8n/t3h8K/wd/f4i+XxsNfvPNN7n6sEmTJm4TxOJeJgEA8A8z9ACAwNMO8kuXLnWzpeG0wZgCr9ZsK8TpeDCVwBcXlUxrYz6t/Vao1kZ3Wmut3eFFM7MK7/o4cOBAN6v76quvuo3mtEzgcGjjud69e7uN9FSqr6PeVDquWW4NIOS3CVxhqeRdgxFawqAQqnPsVRZ/9dVXu83aateu7db9q3RcR7AlJSUd8WMpDGvmX5UVui8NDmgTQoV7Bf1IUlm7wrQ25NNO/Hp+er7q07ffftsNtJx99tl24403Fng/+nnScXmPPvqoWxev9e96rdevX5/rdjqyUJsYajNDDSaEdrPX2npt6AcACDYCPQAg8BSiVXp//fXX5+oLhWaFLe1Or7Xm2l1ewUpr74uDgqA2QdNjaw27Zpp1LFmo5F6b4Smoaqdz3UZHwamMXRvBaUO4w6XvU5DUfgEK1trhXsefKRgePMN+uLTbuja709F5OhpPu7XrzHu1XcfS6fmp1F/9p8GJolBZvcrrdUKAAq9Cro6wU9Bt3LixRVroPHsNWCjAa828SuzVLh17l1d5fH7H/WkfBd2Pll9oUEWDHzoxIUQ7/M+aNcsNvNxwww1uIET7EsyePbvAo/MAAMFQKrugnV8AAAAAAEBMYg09AAAAAAAeItADAAAAAOAhAj0AAAAAAB4i0AMAAAAA4CECPQAAAAAAHiLQAwAAAADgIQI9AAAAAAAeItADAAAAAOAhAj0AAAAAAB4i0AMAAAAA4CECPQAAAAAAHiLQAwAAAABg/vl/mqErZAZKazYAAAAASUVORK5CYII="/>
</div>
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
<h4 id="Brief-interpretation">Brief interpretation<a class="anchor-link" href="#Brief-interpretation">¶</a></h4><p>While the total order value generally has a positive correlation with item count, the trend is non-linear. As baskets get larger, we see diminishing marginal returns in total value. This is likely due to a shift in basket composition: bulk buyers often purchase lower-priced 'add-ons' rather than multiplying high-ticket luxury goods, preventing a linear spike in cost.</p>
<p>Orders with fewer items exhibit the highest variance and extreme right-skewed outliers. This reflects wide variety of products sold in retail behavior. A single item is just as likely to be a high-value electronic (e.g., a laptop) as it is a low-cost consumable (e.g., a pen). As item count increases, the mix of cheap and expensive products naturally averages out the total price, smoothing out the volatility and reducing the range of outliers.</p>
</div>
</div>
</div>
</div>
</main>
</body>
</html>
</div>