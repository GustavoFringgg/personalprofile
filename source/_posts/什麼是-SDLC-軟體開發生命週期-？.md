---
title: SDLC大解惑 (軟體開發生命週期)？
date: 2025-01-26 13:14:47
tags:
  - 網路知識
---

![](https://images.unsplash.com/photo-1508020963102-c6c723be5764?w=500&auto=format&fit=crop&q=60&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8OHx8c2t5fGVufDB8fDB8fHww)

在網路文章充斥著 AI 將會取代軟體工程師的言論中，不經意看到網友說了"能處理整個 SDLC 周期的工程師目前不會被取代"

這段話激起我的好奇心，讓小白的我決定來初步了解何謂 SDLC

<!--more-->

有時候聽到新名詞時，會先餵給 GPT，將大方向確認，再細部深度了解 :　請將 SDLC 概念用白話解釋給一個高中生聽

## 介紹

> SDLC: Software Development Life Cycle，軟體開發生命週期

> <small>想像你要做一個機器人，它能幫你寫作業、煮飯或掃地。但你不能直接造出來
> 而是要先想好怎麼做（規劃）、畫設計圖（設計）、開始組裝（開發）、測試看看有沒有問題（測試）、正式使用（部署）
> 最後還要修修補補讓它更好（維護）。
> 這整個過程就是 SDLC（軟體開發生命週期），它確保我們能有條理地開發出好用的軟體。

## 目的

管理軟體開發流程的方法論，涵蓋從需求分析到系統維護的所有階段
而 SDLC 的底層邏輯就是確保<font color=#FF0000>「軟體開發的可預測性、可控性和品質」</font>

1. 需求分析（Requirement Analysis） - 確認軟體的功能需求與業務需求。
2. 系統設計（System Design） - 定義軟體架構、資料庫設計、技術選擇等。
3. 開發（Development） - 依照設計進行程式碼撰寫。
4. 測試（Testing） - 確保軟體符合需求，沒有重大錯誤。
5. 部署（Deployment） - 將軟體正式上線，提供給使用者。
6. 維護（Maintenance） - 修正錯誤、優化效能或加入新功能。

而 SDLC 的影響是什麼

1. 提高軟體品質：有計畫地開發可以減少錯誤並提高穩定性。
2. 降低開發風險：清楚規劃每個階段，可以避免時間或資源浪費。
3. 提升專案管理效率：讓團隊知道開發的進度，確保軟體按時交付。
4. 確保軟體可維護性：標準化開發流程，使日後擴充或修正變得更容易。

原來是軟體設計的過程，都需要有計畫的開發、執行、檢討，以避免不必要的工時/成本產生

但我想一個完整的產品開發，也不會單純由前後端工程師去包，初步探討後可以分為以下幾列

1. 需求分析（Requirement Analysis）
   📌 負責職稱：
   &nbsp;&nbsp;&nbsp;&nbsp;產品經理（PM）
   &nbsp;&nbsp;&nbsp;&nbsp;業務分析師（BA）
   &nbsp;&nbsp;&nbsp;&nbsp;客戶（Client/Stakeholder）
   📌 職責：
   &nbsp;&nbsp;&nbsp;&nbsp;確定軟體要解決的問題和功能需求
   &nbsp;&nbsp;&nbsp;&nbsp;撰寫需求規格（SRS, Software Requirement Specification）
   &nbsp;&nbsp;&nbsp;&nbsp;討論業務邏輯，確保符合使用者需求
2. 系統設計（System Design）
   📌 負責職稱：
   &nbsp;&nbsp;&nbsp;&nbsp;系統架構師
   &nbsp;&nbsp;&nbsp;&nbsp;資料庫工程師
   &nbsp;&nbsp;&nbsp;&nbsp;後端
   &nbsp;&nbsp;&nbsp;&nbsp;UI/UX 設計師
   📌 職責：
   &nbsp;&nbsp;&nbsp;&nbsp;設計系統架構（Monolithic、Microservices、Serverless）
   &nbsp;&nbsp;&nbsp;&nbsp;規劃資料庫結構（ERD, Entity-Relationship Diagram）
   &nbsp;&nbsp;&nbsp;&nbsp;定義 API 規格與前後端接口
   &nbsp;&nbsp;&nbsp;&nbsp;UI/UX 設計，使用 Figma 或 Adobe XD 設計前端畫面
3. 開發（Development）
   📌 負責職稱：
   &nbsp;&nbsp;&nbsp;&nbsp;前端/後端
   &nbsp;&nbsp;&nbsp;&nbsp;行動應用工程師
   &nbsp;&nbsp;&nbsp;&nbsp;DevOps 工程師（負責 CI/CD 流程）
   📌 職責：
   &nbsp;&nbsp;&nbsp;&nbsp;前端開發
   &nbsp;&nbsp;&nbsp;&nbsp;後端 API 開發
   &nbsp;&nbsp;&nbsp;&nbsp;整合資料庫與 API
   &nbsp;&nbsp;&nbsp;&nbsp;設置 CI/CD 流程，確保自動化部署
4. 測試（Testing）
   📌 負責職稱：
   &nbsp;&nbsp;&nbsp;&nbsp;軟體測試工程師
   &nbsp;&nbsp;&nbsp;&nbsp;自動化測試工程師
   &nbsp;&nbsp;&nbsp;&nbsp;開發工程師（負責單元測試）
   📌 職責：
   &nbsp;&nbsp;&nbsp;&nbsp;撰寫測試計畫與測試案例
   &nbsp;&nbsp;&nbsp;&nbsp;執行單元測試與整合測試（Integration Testing）
   &nbsp;&nbsp;&nbsp;&nbsp;自動化測試（使用 Cypress、Selenium 等工具）
   &nbsp;&nbsp;&nbsp;&nbsp;進行壓力測試與資安測試
5. 部署（Deployment）
   📌 負責職稱：
   &nbsp;&nbsp;&nbsp;&nbsp;DevOps 工程師
   &nbsp;&nbsp;&nbsp;&nbsp;後端
   📌 職責：
   &nbsp;&nbsp;&nbsp;&nbsp;部署軟體到伺服器或雲端（AWS、Azure、GCP）
   &nbsp;&nbsp;&nbsp;&nbsp;設定 CI/CD 流程，確保自動化部署
   &nbsp;&nbsp;&nbsp;&nbsp;監控系統運行狀況，確保穩定性
6. 維護（Maintenance）
   📌 負責職稱：
   &nbsp;&nbsp;&nbsp;&nbsp;後端/後端
   &nbsp;&nbsp;&nbsp;&nbsp;SRE（Site Reliability Engineer）
   📌 職責：
   &nbsp;&nbsp;&nbsp;&nbsp;修復 Bug，提升軟體效能
   &nbsp;&nbsp;&nbsp;&nbsp;部署安全性更新
   &nbsp;&nbsp;&nbsp;&nbsp;監控系統運作（使用 Grafana、Prometheus 等工具）
   &nbsp;&nbsp;&nbsp;&nbsp;進行版本更新與新功能開發

看起來安全又完善的開發規範，但一定會有它的潛在風險對吧?對吧?
這也牽扯了許多開發的模型(瀑布式開發、敏捷式開發)，團隊依開發模型的取捨，也有相對應的風險

## 風險

1. ❌❌ 缺乏彈性（特定模型問題）
   缺點：傳統 SDLC（如瀑布模型）的階段是線性進行的，一旦進入下一個階段，就很難回頭修改需求或設計。
   影響：如果需求在開發過程中變更，可能需要重做前面幾個步驟，導致時間與成本增加。
2. ❌❌ 開發週期長，前期準備繁瑣
   缺點：完整的 SDLC 需要詳細的需求分析、設計與測試，這會增加開發時間，特別是大型專案。
   影響：對於快速變動的市場，過長的開發周期可能會讓產品過時或錯失商機。
3. ❌❌ 高開發成本
   缺點：完整遵循 SDLC 需要投入大量時間與人力，如需求分析、測試、維護等，成本較高。
   影響：對於小型企業或新創公司來說，完整 SDLC 可能會佔用過多資源，不符合成本效益。
4. ❌❌ 測試通常發生在開發後期
   缺點：在傳統 SDLC（如瀑布模型）中，測試通常是在開發完成後才開始，這可能導致晚期發現重大錯誤，修復成本高。
   影響：錯誤發現得太晚，可能會影響整體專案進度。
5. ❌❌ 需求不確定時難以應對
   缺點：SDLC 假設需求是固定且明確的，但實際上，客戶需求可能會不斷變更，這對 SDLC（特別是瀑布模型）來說是個挑戰。
   影響：需求變更可能導致專案延遲、成本上升，甚至失敗。

雖然 SDLC 是標準開發方法，但理想總是豐滿、現實總是骨感，我想最重要的就是想辦法讓自己保有最大的彈性，唯一的不變就是變。
