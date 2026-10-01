+++
title = "Kubernetes 筆記：Pod 排程"
date = 2026-09-10T09:00:00+08:00
tags = ["kubernetes", "infra"]
cover = "cover.svg"
summary = "整理 kube-scheduler 如何挑選節點的核心機制。"
+++

kube-scheduler 會依序經過 filtering 與 scoring 兩個階段，
選出最適合執行 Pod 的節點。

## Filtering

先篩除不符合資源需求或 taint/toleration 限制的節點。

## Scoring

再對剩下的節點評分，挑出分數最高者進行綁定。
