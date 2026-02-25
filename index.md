---
layout: default
title: Project Overview
nav_order: 1
---

# E-Commerce Customer Behavior Report  
<div style="margin-bottom: 1rem;"></div>
This report documents the end-to-end data science workflow applied to an e-commerce orders dataset, starting from the raw data and extracting patterns and insights through both supervised and unsupervised learning. A quick summary below details the steps taken for this workflow.
<div style="margin-bottom: 2rem;"></div>
[**Data Preprocessing (Phase 1)**]({{ '/docs/phase1.html' | relative_url }}) — Four raw relational tables (`orders`, `order_items`, `order_shipping`, `payments`) were consolidated into a single order-level analytical record. The pipeline addressed missing values via statistical imputation (median for numerical, mode for categorical), enforced logical business constraints (valid monetary and quantity fields), and engineered derived features including `order_value_per_item` and `order_size_category`. The result was a clean, deduplicated dataset persisted as `ecommerce_orders_cleaned.csv`.

[**Supervised Learning (Phase 2)**]({{ '/docs/phase2.html' | relative_url }}) — Classification models (Logistic Regression, Decision Tree, and Random Forest) were trained to predict the payment method (`payment_type`) from order attributes. After encoding and scaling, Random Forest delivered the strongest performance across all evaluation metrics, with its ensemble structure providing robustness against class imbalance and capturing the non-linear patterns that characterize real-world transaction data.

[**Unsupervised Learning (Phase 3)**]({{ '/docs/phase3.html' | relative_url }}) — Documented in full in this notebook. K-Means clustering (k = 4) segmented orders into four behaviorally distinct groups defined primarily by basket value and freight intensity. Market Basket Analysis then surfaced high-lift associations between product categories, payment types, and order sizes — most notably the strong link between large orders, furniture/decor categories, and credit card payment. Together, these findings translate raw transactional data into actionable customer segments and cross-sell intelligence.
<div style="margin-bottom: 1rem;"></div>
**Contributors:**  

<div style="display: flex; flex-wrap: wrap; gap: 1.5rem; margin-top: 1rem;">
    <!-- Person 1 -->
    <div style="flex: 1 1 calc(50% - 1rem); max-width: calc(50% - 1rem); padding: 1rem; border-radius: 8px; background: #fafafa;">
        <div style="display: flex; align-items: center;">
        <img src="{{ '/assets/images/aaron.jpeg' | relative_url }}" 
            alt="Aaron Chou" 
            width="60" 
            style="border-radius: 50%; margin-right: 12px;">
        <div>
            <a href="https://www.linkedin.com/in/aaron-c-82b546159/" target="_blank" rel="noopener">Aaron Chou</a><br>
            <small>IT Analyst</small>
        </div>
        </div>
    </div>
    <!-- Person 2 -->
    <div style="flex: 1 1 calc(50% - 1rem); max-width: calc(50% - 1rem); padding: 1rem; border-radius: 8px; background: #fafafa;">
        <div style="display: flex; align-items: center;">
        <img src="{{ '/assets/images/javier.png' | relative_url }}" 
            alt="Javier Lee" 
            width="60" 
            style="border-radius: 50%; margin-right: 12px;">
        <div>
            <a href="https://www.linkedin.com/in/javier-lee-a307731b3/" target="_blank" rel="noopener">Javier Lee</a><br>
            <small>Data Scientist</small>
        </div>
        </div>
    </div>
    <!-- Person 3 -->
    <div style="flex: 1 1 calc(50% - 1rem); max-width: calc(50% - 1rem); padding: 1rem; border-radius: 8px; background: #fafafa;">
        <div style="display: flex; align-items: center;">
        <img src="{{ '/assets/images/jayden.jpeg' | relative_url }}" 
            alt="Jayden Liaw" 
            width="60" 
            style="border-radius: 50%; margin-right: 12px;">
        <div>
            <a href="https://www.linkedin.com/in/liawjianwei/" target="_blank" rel="noopener">Jayden Liaw</a><br>
            <small>ML Engineer</small>
        </div>
        </div>
    </div>
    <!-- Person 4 -->
    <div style="flex: 1 1 calc(50% - 1rem); max-width: calc(50% - 1rem); padding: 1rem; border-radius: 8px; background: #fafafa;">
        <div style="display: flex; align-items: center;">
        <img src="{{ '/assets/images/leechuan.jpeg' | relative_url }}" 
            alt="Lee Chuan" 
            width="60" 
            style="border-radius: 50%; margin-right: 12px;">
        <div>
            <a href="https://www.linkedin.com/in/aleechuan/" target="_blank" rel="noopener">Lee Chuan</a><br>
            <small>Software Engineer</small>
        </div>
        </div>
    </div>

</div>