---
description: na
keywords: na
title: Scenario - Executives Securely Exchange Privileged Information
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e18cf5df-859e-4028-8d19-39b0842df33d
---
# 案例 - 主管安全地交換機密資訊
本節包含系統管理員指示，以及使用者指示的指引。您必須先完成對系統管理員的指示，然後再告知使用者這個組態。

## 系統管理員的指示
![](../Image/AzRMS_AdminBanner.png)

使用這些指示可讓主管安全地互換電子郵件與電子郵件附件，並有原則會自動限制主管的存取，完全不需要他們採取任何特殊動作。這些電子郵件及所有附件均由 Azure Rights Management 提供保護。

指示適用於下列一組情況：

-   主管可以互相交換與對他人保密的機密資訊。

-   主管在傳送這些電子郵件時，除了必須將郵件傳送到公司電子郵件地址，而不能傳送到個人電子郵件地址之外，其餘都與一般傳送作業相同。

## 此案例的需求
此案例要能運作，必須滿足下列條件：

|Check|需求|如果需要更多資訊|
|---------|------|------------|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|備妥 Office 365 或 Azure Active Directory 的帳戶與群組：<br /><br />-   具備郵件功能的群組 (名為**主管**)<br />-   所有主管都是**主管**群組的成員|[準備 Azure Rights Management](https://technet.microsoft.com/library/jj585029.aspx)|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|您的 Azure Rights Management 租用戶金鑰由 Microsoft 管理；您不會使用 BYOK|[規劃及實作 Azure Rights Management 租用戶金鑰](https://technet.microsoft.com/library/dn440580.aspx)|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|Azure Rights Management 已啟動|[啟用 Azure Rights Management](https://technet.microsoft.com/library/jj658941.aspx)|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|Azure Rights Management 會啟用 Exchange Online|展開 [Exchange Online：IRM 組態](https://technet.microsoft.com/library/jj585031.aspx)一節 (位於[針對 Azure Rights Management 設定應用程式](https://technet.microsoft.com/library/jj585031.aspx))。|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|您已如下所述設定自訂範本|[設定 Azure Rights Management 的自訂範本](https://technet.microsoft.com/library/dn642472.aspx)|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif)|您已如下所述設定 IRM 的傳輸保護規則|[建立傳輸保護規則](https://technet.microsoft.com/library/dd302432.aspx)|

#### 若要設定主管電子郵件的自訂範本：

1.  在 Azure 入口網站中：為 Azure Rights Management 建立新的自訂範本，其中包含下列值及設定：

    -   名稱：**主管**

    -   權限：將 [共同擁有者] 權限授與具備郵件功能的「主管」群組

2.  發行新範本。

3.  使用 Exchange Online 的 Windows PowerShell 命令，重新整理 Exchange Online 的範本：

    ```
    Import-RMSTrustedPublishingDomain -Name "RMS Online -1" -RefreshTemplates –RMSOnline
    ```

#### 若要設定自動保護主管所接收及傳送的電子郵件：

-   在 Exchange 系統管理中心中：建立新的郵件流程規則，其中包含下列值及設定:

    -   按一下新增圖示，然後選取 [套用權限保護至郵件]

    -   在 [新增規則] 頁面上：

        -   指定名稱，例如**將主管範本套用至主管電子郵件**

        -   對於 [若為以下情況，套用這個規則]，選取 [寄件者.... 是此群組的成員]，然後選取 [主管]。

        -   按一下 [新增條件]，選取 [收件者.... 是此群組的成員]，然後選取 [主管]。

        -   對於 [執行下列動作]，確定已選取 [將權限保護套用到具有下列條件的郵件]，然後按一下 [選取一個]，以選取 [主管] 範本。

        -   確定已選取 [選擇用於此規則的模式]、[強制]。

        -   按一下 [儲存]。

## 使用者指示
此案例因為不需要主管執行任何特殊的動作來保護其所接收及傳送的電子郵件，所以沒有特定的使用者指示。電子郵件訊息及所有附件均會自動受到保護，只允許 [主管] 群組的成員進行存取。但您可能需要告知主管與技術支援人員這些電子郵件會自動受到保護，以及他們在使用這類電子郵件時的限制。例如若將這類電子郵件或附件轉寄給他人，他人可能無法順利閱讀。

完成此案例的 Exchange Online 之後，可以傳送下列標準電子郵件通訊範例給主管。

### 範例使用者文件
![](../Image/AzRMS_ExampleBanner.png)

##### IT 公告：主管電子郵件現在會自動施以保護

-   從現在起，當您傳送電子郵件給公司的另一位主管時，電子郵件及任何附件的內容都會自動施以保護，只有公司的該名收件主管才能存取，進而閱讀其資訊、列印、複製其中的內容及執行其他作業等等。當您將電子郵件訊息轉寄給其他人或儲存附件時，也同樣會套用此限制。此項保護有助於防止機密或敏感資訊的資料遺失。

    請注意，若您希望他人也能閱讀及編輯這些電子郵件中的資訊，您必須個別傳送電子郵件給這些人。

    將公司機密資訊傳送給另一位主管時，請務必傳送到該主管的公司電子郵件地址，而不是個人電子郵件地址。

**需要協助嗎？**

-   請連絡技術支援人員：helpdesk@vanarsdelltd.com

