---
description: na
keywords: na
title: Scenario - Retain Control of Documents Stored in SharePoint
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1b6244c7-5ab9-4881-bc8f-6fa960390d89
---
# 案例 - 保留對儲存在 SharePoint 中文件的控制
本節包含系統管理員指示，以及使用者指示的指引。您必須先完成對系統管理員的指示，然後再告知使用者這個組態。

## 系統管理員的指示
![](../Image/AzRMS_AdminBanner.png)

使用這些指示可透過受保護的文件庫，確保您能夠控制儲存在 SharePoint 中的 Office 文件。例如，文件會自動施以保護，以避免使用者蓄意或意外洩漏，同時還能在文件下載或同步處理之後，封鎖對內容的存取。需要保護的檔案可能會是需要共同作業的設計文件或計畫，也可能屬於交付項目。當您設定 SharePoint 的受保護文件庫時，其中所儲存的 Office 檔案會由 Azure Rights Management 提供保護。

指示適用於下列一組情況：

-   員工共用及合作處理 Office 文件。

-   文件包含非公開但不一定是內部專用的資訊。

-   對於系統管理員在文件庫層級所設定的權限，員工無須設定或變更。

## 此案例的需求
此案例要能運作，必須滿足下列條件：

|Check|需求|如果需要更多資訊|
|---------|------|------------|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|您已針對 Office 365 或 Azure Active Directory 準備帳戶和群組|[準備 Azure Rights Management](https://technet.microsoft.com/library/jj585029.aspx)|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|Azure Rights Management 已啟動|[啟用 Azure Rights Management](https://technet.microsoft.com/library/jj658941.aspx)|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|若要使用 SharePoint Server：部署 RMS 連接器，並針對 SharePoint 加以設定|[部署 Azure Rights Management 連接器](https://technet.microsoft.com/library/dn375964.aspx)|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|設定 SharePoint 的 IRM 及受保護文件庫|[在 SharePoint 系統管理中心設定資訊版權管理 (IRM)](https://support.office.com/en-us/article/Set-up-Information-Rights-Management-IRM-in-SharePoint-admin-center-239ce6eb-4e81-42db-bf86-a01362fed65c)<br /><br />[將資訊版權管理套用至清單或程式庫](http://office.microsoft.com/sharepoint-help/apply-information-rights-management-to-a-list-or-library-HA102891460.aspx)|

## 使用者指示
此案例因為不需要使用者執行任何特殊的動作，所以沒有特定的使用者指示。文件會依據 SharePoint 系統管理員為網站設定的權限而自動受到保護。但您可能需要告知使用者與技術支援人員哪些文件庫受到保護，以及他們在使用這類文件時的限制。例如目前的限制可能會讓文件只能在行動裝置上檢視而無法編輯。

當將 SharePoint 文件庫設定為使用 Azure RMS 之後，可以傳送下列標準電子郵件通訊範例給相關部門或小組。

### 範例使用者文件
![](../Image/AzRMS_ExampleBanner.png)

##### IT 公告：變更銷售預測與報表網站

-   SharePoint **銷售預測與報表**網站現在已設有保護，可安全地共同作業。從現在起，您只能直接編輯儲存在此網站中的試算表與 Word 文件；例如，您無法將文件儲存到其他位置稍後編輯，也無法透過電子郵件傳送給他人。您可以使用行動裝置檢視這類文件，但必須使用 Windows 電腦才能編輯。

**需要協助嗎？**

-   請連絡技術支援人員：helpdesk@vanarsdelltd.com

