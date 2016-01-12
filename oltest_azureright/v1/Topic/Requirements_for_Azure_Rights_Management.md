---
description: na
keywords: na
title: Requirements for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dc78321d-d759-4653-8818-80da74b6cdeb
---
# Azure Rights Management 的需求
若要在組織中部署 Microsoft Azure Rights Management (Azure RMS)，請確定您具備下列必要條件。 您接著可使用[Azure Rights Management 部署藍圖](../Topic/Azure_Rights_Management_Deployment_Roadmap.md)來部署您組織的 Rights Management。

|需求|詳細資訊|
|------|--------|
|RMS 的雲端訂閱|您的組織必須具有支援 RMS 的雲端訂閱。<br /><br />如需授權資訊，請參閱本主題中的＜[支援 Azure RMS 的雲端訂閱](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions)＞一節。|
|Azure AD 目錄|您的組織必須具備 Azure AD 目錄才能支援 RMS 的使用者驗證。 此外，若要從內部部署目錄 (AD DS) 使用您的使用者帳戶，您也必須設定目錄整合。<br /><br />當您有必要的用戶端軟體且正確設定 MFA 支援基礎結構時，Azure RMS 就支援 Multi-Factor Authentication (MFA)。<br /><br />如需詳細資訊，請參閱本主題中的 [Azure AD 目錄](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_AzureADTenant)一節。|
|用戶端裝置|使用者必須擁有執行支援 RMS 作業系統的用戶端裝置 (電腦或行動裝置)。<br /><br />如需詳細資訊，請參閱本主題中的＜[支援 Azure RMS 的用戶端裝置](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedDevices)＞一節。|
|應用程式|使用者必須執行支援 RMS 的應用程式。<br /><br />如需詳細資訊，請參閱本主題中的＜[支援 Azure RMS 的應用程式](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedApplications)＞一節。|
|支援連線至網際網路和相依雲端服務的基礎結構|如果您有防火牆或類似介入網路裝置，必須設定為允許特定的連線，請參閱＜[Office 356 URL 和 IP 位址範圍](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)＞。<br /><br />**[Office 365 入口網站與身分識別]** 區段所列出的 URL 和 IP 位址適用於 Office 365 入口網站、Azure Active Directory 資源和 Azure Rights Management。 使用本文章的指示，藉由訂閱 RSS 摘要追蹤此資訊的最新變更。<br /><br />除了 Office 文章中的資訊，還有 Azure RMS 特有資訊：<br /><br />-   請勿終止 TLS 用戶端對服務連線 (例如，為了執行封包層級檢查)。 這麼做會中斷 RMS 用戶端為了保護自己與 Azure RMS 的通訊，而對 Microsoft 所管理的 CA 進行的憑證偵測。<br />-   請勿使用代表使用者進行驗證的 Web Proxy 設定。|

若要搭配使用 Azure RMS 與內部部署伺服器，則會支援下列產品：

-   Exchange Server

-   SharePoint Server

-   支援檔案分類基礎結構的 Windows Server 檔案伺服器

如需此案例的其他 Azure RMS 需求的詳細資訊，請參閱本主題中的＜[支援 Azure RMS 的內部部署伺服器](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedServers)＞一節。

> [!IMPORTANT]
> 不支援下列部署案例：
> 
> -   在相同組織中同時執行 AD RMS 和 Azure RMS (移轉期間除外)，如[從 AD RMS 移轉至 Azure Rights Management](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md) 所述。
> 
> 支援[從 AD RMS 到 Azure RMS](http://technet.microsoft.com/library/Dn858447.aspx)，以及從 [Azure RMS 到 AD RMS](http://msdn.microsoft.com/library/azure/dn629429.aspx) 的移轉路徑。 如果您部署 Azure RMS，然後決定您不再想要使用此雲端服務，請參閱＜[解除委任並停用 Azure Rights Management](../Topic/Decommissioning_and_Deactivating_Azure_Rights_Management.md)＞。

請使用下列各節以深入了解 Azure RMS 需求。

## <a name="BKMK_SupportedSubscriptions"></a>支援 Azure RMS 的雲端訂閱
若要使用 Azure RMS，您的組織必須至少有一個下列訂閱，且訂閱需具有可保護檔案和電子郵件訊息的足夠使用者和服務授權數目。 如果您有服務將對使用者 (檔案或電子郵件訊息的擁有者) 套用保護，這些使用者需要這些授權的其中一個。 只會使用 (例如讀取及編輯) 此受保護資料的使用者不需要授權。

-   Office 365

-   Azure Rights Management Premium (先前稱為 Azure RMS Standalone)

-   Enterprise Mobility Suite

-   個人版 RMS

如需詳細資訊及申請選項的詳細資訊，請使用下列各節。

如需授權的付費訂閱的 Azure RMS 功能比較，請參閱 [Rights Management Services (RMS) 產品項目的比較](http://technet.microsoft.com/dn858608)。

### Office 365 訂閱
[免費 30 天試用：企業版 E3](http://go.microsoft.com/fwlink/p/?LinkID=403802)

此訂閱是對想要使用 Office 線上服務及使用其資訊版權管理功能 (使用 Azure RMS) 的組織所設計。 不過，並非所有 Office 365 訂用帳戶皆包括 Azure RMS。

|授權選項|Office 365 商務基本版|Office 365 商務進階版|Office 365 企業版 E1<br /><br />Office 365 教育版 A1|Office 365 企業版 E3<br /><br />Office 365 教育版 A3<br /><br />Office 365 Government G3|Office 365 企業版 E4<br /><br />Office 365 教育版 A4<br /><br />Office 365 政府版 G4|Office 365 企業版 E5<br /><br />Office 365 教育版 A5<br /><br />Office 365 政府版 G5|Office 365 Enterprise K1|SharePoint 方案 1<br />SharePoint 方案 2|Exchange Online 方案 1<br />Exchange Online 方案 2|
|--------|--------------------|--------------------|------------------------------------------|----------------------------------------------------------------------|---------------------------------------------------------------|---------------------------------------------------------------|----------------------------|------------------------------------|----------------------------------------------|
|資訊版權保護 (IRM)|否|否|否|是|是|是|否|否|否|

### Azure Rights Management Premium 訂用帳戶
[免費 30 天試用](https://portal.microsoftonline.com/Signup/MainSignUp15.aspx?&amp;OfferId=A43415D3-404C-4df3-B31B-AAD28118A778&amp;dl=RIGHTSMANAGEMENT&amp;ali=1)

此訂用帳戶先前稱為 Azure RMS Standalone，如果組織想要使用 Azure RMS，但不具有包含 Azure RMS 的訂用帳戶，就適合使用這個訂用帳戶。 例如，若您有 Office 365 商務基本版或 Office 365 Enterprise E1 訂用帳戶，這些訂用帳戶不會支援 Azure RMS (請參閱上一節的表格)。 若要使用 Azure RMS，您可購買 Azure Rights Management Premium 訂用帳戶 (或購買其他訂用帳戶，例如包含 Azure RMS 的 Office 365 Enterprise E4)。

如需詳細資訊，請參閱 [Microsoft Azure Rights Management](http://products.office.com/business/microsoft-azure-rights-management)。

此訂閱也提供試用期讓您免費試用 Azure RMS，人數是 25 個使用者。 如果在您購買更換的訂閱之前訂閱就過期，請參閱下一節＜試用訂閱過期時會發生什麼事？＞。

|授權選項|Office 365 商務基本版|Office 365 商務進階版|Office 365 企業版 E1<br /><br />Office 365 教育版 A1|Office 365 企業版 E3<br /><br />Office 365 教育版 A3<br /><br />Office 365 Government G3|Office 365 企業版 E4<br /><br />Office 365 教育版 A4<br /><br />Office 365 政府版 G4|Office 365 企業版 E5<br /><br />Office 365 教育版 A5<br /><br />Office 365 政府版 G5|Office 365 Enterprise K1|SharePoint 方案 1<br />SharePoint 方案 2|Exchange Online 方案 1<br />Exchange Online 方案 2|
|--------|--------------------|--------------------|------------------------------------------|----------------------------------------------------------------------|---------------------------------------------------------------|---------------------------------------------------------------|----------------------------|------------------------------------|----------------------------------------------|
|資訊版權保護 (IRM)|是|是 <sup>1</sup>|是|是|是|是|是|是|是|
<sup>1</sup> 針對商務進階版，有一些用戶端限制：您可以使用 Outlook Web App 及 RMS 共用應用程式保護內容，並透過 RMS 使用受保護的內容。 您可以使用所有其他的 Office 應用程式 (包括 Office Online 以及 Office 365 商務進階版的用戶端應用程式) 使用受保護的內容。

#### <a name="BKMK_TrialExpiryBehavior"></a>試用訂閱過期時會發生什麼事？
如果試用訂閱過期，您將無法存取以 Azure RMS 試用訂閱所保護的內容。 不過，如果您購買支援 Azure RMS 的訂閱，就會自動還原存取權。

例外情況是如果在您取得試用訂閱之前，組織就已使用 Azure RMS 與個人版 RMS 訂閱，則不會在過期時喪失存取權。 所以，即使試用訂閱過期，仍然可以存取先前保護的內容。

### Enterprise Mobility Suite 訂閱
[免費 30 天試用](http://go.microsoft.com/fwlink/?LinkId=615385)

此訂閱是對想要使用 Azure Active Directory Premium、Windows Intune 和 Azure Rights Management 組合的組織所設計。 如需詳細資訊，請參閱 [Microsoft 企業行動化概觀](http://go.microsoft.com/fwlink/?LinkId=615386)。

|授權選項|Office 365 商務基本版|Office 365 商務進階版|Office 365 企業版 E1<br /><br />Office 365 教育版 A1|Office 365 企業版 E3<br /><br />Office 365 教育版 A3<br /><br />Office 365 Government G3|Office 365 企業版 E4<br /><br />Office 365 教育版 A4<br /><br />Office 365 政府版 G4|Office 365 企業版 E5<br /><br />Office 365 教育版 A5<br /><br />Office 365 政府版 G5|Office 365 Enterprise K1|SharePoint 方案 1<br />SharePoint 方案 2|Exchange Online 方案 1<br />Exchange Online 方案 2|
|--------|--------------------|--------------------|------------------------------------------|----------------------------------------------------------------------|---------------------------------------------------------------|---------------------------------------------------------------|----------------------------|------------------------------------|----------------------------------------------|
|資訊版權保護 (IRM)|是|是 <sup>1</sup>|是|是|是|是|是|是|是|
<sup>1</sup> 針對商務進階版，有一些用戶端限制：您可以使用 Outlook Web App 及 RMS 共用應用程式保護內容，並透過 RMS 使用受保護的內容。 您可以使用所有其他的 Office 應用程式 (包括 Office Online 以及 Office 365 商務進階版的用戶端應用程式) 使用受保護的內容。

### 個人版 RMS 訂閱
這是對尚未部署 Azure RMS 或 AD RMS 的組織中個人所設計的訂閱。 此可讓這些人員閱讀正在使用 Azure RMS 的組織所保護的內容，而他們也能保護其本身的內容。

如需詳細資訊，請參閱[個人版 RMS 和 Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md)。

## <a name="BKMK_AzureADTenant"></a>Azure AD 目錄
您必須有 Azure AD 目錄才能使用 Azure RMS。 您可為此目錄使用您的組織帳戶來登入 Azure 傳統入口網站，例如，您可設定和管理 Rights Management 範本。

如果您的組織尚無 Azure 訂閱，您可以註冊免費試用以取得訂閱：移至 [Azure 快速入門](https://account.windowsazure.com/organization)頁面，並依照指示進行。

如需詳細資訊，請參閱 Azure Active Directory 文件的下列資源：

-   [什麼是 Azure AD 目錄？](http://msdn.microsoft.com/en-us/library/185da266-58a9-43e6-9c66-2c8f702545c6)

-   [Azure 訂閱與 Azure AD 的關聯方式](http://msdn.microsoft.com/en-us/library/edf05c2e-944a-4da5-a330-dc9dc479f127)

若要整合 Azure AD 目錄與內部部署 AD 樹系，請參閱[目錄整合](http://msdn.microsoft.com/en-us/library/bf82bdff-2467-403b-8c1a-0e9eebcf31e8)。

> [!NOTE]
> 如果您擁有的行動裝置或 Mac 電腦使用 AD FS 或同等的驗證提供者來驗證內部部署：
> 
> -   您必須使用在最低伺服器版本的 **Windows Server 2012 R2** 上運作的 AD FS，或使用支援 OAuth 2.0 通訊協定的替代驗證提供者。

### <a name="BKMK_MFA"></a>Multi-Factor Authentication (MFA) 和 Azure RMS
若要使用 Multi-Factor Authentication (MFA) 與 Azure RMS，至少需要下列其中一項：

-   Office 2013 (最低版本)：

    -   如果您有 Office 2013，您也必須安裝 [Office 2013 更新 2015 年 6 月 9 日 (KB3054853)](https://support.microsoft.com/kb/3054853)。 如需有關此更新以及現代化驗證如何將 Active Directory Authentication Library (ADAL) 引進 Office 2013 的詳細資訊，請參閱 Office 部落格上的[宣布 Office 2013 現代化驗證公用預覽](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/)。

-   適用於 Windows 的 Rights Management 共用應用程式：

    -   您必須已安裝最低版本 1.0.1908.0，可使用 [控制台]、[程式和功能] 來確認。 如需有關共用應用程式的詳細資訊，請參閱[適用於 Windows 的 Rights Management 共用應用程式](../Topic/Rights_Management_Sharing_Application_for_Windows.md)。

-   還有適用於行動裝置和 Mac 電腦的 Rights Management 共用應用程式：

    -   確定您已安裝最新版本。 RMS 共用應用程式 2015 年 9 月份版本引進 MFA 支援。

然後，設定 MFA 解決方案：

-   Microsoft 管理的租用戶 (您有 Azure Active Directory 或 Office 365)：

    -   設定 Azure MFA 對使用者強制執行 MFA。 如需相關指示，請參閱 Azure 文件中的[開始在雲端中使用 Azure Multi-Factor Authentication](https://azure.microsoft.com/documentation/articles/multi-factor-authentication-get-started-cloud/)。

        如需 Azure MFA 的詳細資訊，請參閱[什麼是 Azure Multi-Factor Authentication？](https://azure.microsoft.com/documentation/articles/multi-factor-authentication/)。

-   同盟租用戶 (您操作內部部署的同盟伺服器)：

    -   為 Azure Active Directory 或 Office 365 設定同盟伺服器。例如，如果您使用 AD FS，請參閱 TechNet 上的[設定 AD FS 的其他驗證方法](https://technet.microsoft.com/library/dn758113.aspx)。

        如需此案例的詳細資訊，請參閱 Office 部落格上的[「使用 Office 365 – 身分識別」計畫現在已簡化](https://blogs.office.com/2014/01/30/the-works-with-office-365-identity-program-now-streamlined/)。

## <a name="BKMK_SupportedDevices"></a>支援 Azure RMS 的用戶端裝置
請使用下列各節來識別哪些裝置支援 Azure Rights Management (RMS) 及其支援的 RMS 功能：

-   [電腦](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_RMSSupportedComputers)

-   [行動裝置](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_RMSSupportedMobileDevices)

-   [用戶端裝置功能](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_ClientCapabilities)

### <a name="BKMK_RMSSupportedComputers"></a>電腦
下列電腦作業系統支援 Azure Rights Management：

-   **Windows 7** (x86、x64)

-   **Windows 8** (x86、x64)

-   **Windows 8.1** (x86、x64)

-   **Windows 10** (x86、x64)

-   **Mac OS X**：Mac OS X 10.8 的最低版本 (Mountain Lion)

### <a name="BKMK_RMSSupportedMobileDevices"></a>行動裝置
下列行動裝置作業系統支援 Azure Rights Management：

-   **Windows Phone**：Windows Phone 8.1

-   **Android 手機和平板電腦**：Android 4.0.3 的最低版本

-   **iPhone 和 iPad**：iOS 7.0 的最低版本

-   **Windows RT 平板電腦**：Windows 8 RT、Windows 8.1 RT

### <a name="BKMK_ClientCapabilities"></a>用戶端裝置功能
並非所有受支援的用戶端裝置目前都支援所有 RMS 功能。 請利用下表來識別哪些應用程式支援 RMS 功能及例外情況。

除非另外註明，否則支援的功能適用於 Azure RMS 與 AD RMS 兩者。 此外，在 iOS、Android、OS X 和 Windows Phone 8.1 上的 AD RMS 支援需要 [Active Directory 權限管理服務行動裝置延伸模組](http://technet.microsoft.com/library/a69ead9d-7dd3-4b38-9830-4728e9757341)。

表格欄位的相關資訊：

-   **保護 PDF**：這些檔案具有 .ppdf 副檔名，而且會在您使用 RMS 共用應用程式來透過電子郵件共用 Office 檔案和 PDF 檔案時自動建立。 RMS 共用應用程式含有用來讀取受保護的 PDF 檔案的閱讀程式。 如果您之前使用 Azure RMS 或 AD RMS 建立保護的 PDF 檔案，您可以繼續在 Windows、iOS 和 Android 裝置上，使用 Foxit Reader 和 Nitro Pro 讀取這些檔案。

-   **電子郵件：**列出的電子郵件用戶端可以保護電子郵件訊息本身，這樣會自動保護任何附加檔案。 在此情況下，用戶端的預覽功能可讓授權的收件者看見受保護的內容 (訊息和附件)。 不過，若電子郵件訊息本身未受保護，但附件受到保護，則用戶端預覽功能無法讓授權的收件者看見受保護的附件。

-   **其他檔案類型**：文字和影像檔包含副檔名為 .txt、.xml、.jpg 和 .jpeg 的檔案。 這些檔案在受到 RMS 原生保護後會變更其副檔名並成為唯讀狀態。 無法受到原生保護的檔案在 RMS 對其進行一般保護後，會有 .pfile 副檔名。 如需詳細資訊，請參閱 [Rights Management 共用應用程式系統管理員指南](http://technet.microsoft.com/library/dn339003%28v=ws.10%29.aspx)中的[保護層級 – 原生與一般](https://technet.microsoft.com/library/dn339003.aspx)和[支援的檔案類型和副檔名](https://technet.microsoft.com/library/dn339003.aspx)這兩個章節。

|**裝置作業系統**|Word、Excel、PowerPoint|受保護的 PDF|電子郵件|其他檔案類型|
|--------------|-------------------------|------------|--------|----------|
|**訊息**|Office 2010<br /><br />Office 2013<br /><br />Office Mobile 應用程式(僅適用於 AD RMS) <sup>1</sup><br /><br />Office Online<sup>2</sup>|Gaaiho Doc<br /><br />GigaTrust Desktop PDF Client for Adobe<br /><br />Foxit Reader<br /><br />Nitro PDF 閱讀程式<br /><br />RMS 共用應用程式|Outlook 2010<br /><br />Outlook 2013<br /><br />Outlook Web App (OWA)<sup>3</sup><br /><br />Windows Mail<sup>4</sup>|適用於 Windows 的 RMS 共用應用程式：文字、影像、pfile<br /><br />Siemens JT2Go：JT 檔案 (僅限 Windows 10)|
|**iOS**|Office for iPad and iPhone<sup>5</sup><br /><br />Office Online<sup>2</sup><br /><br />TITUS 文件|Foxit Reader<br /><br />RMS 共用應用程式 <sup>1</sup><br /><br />TITUS 文件|NitroDesk<sup>4</sup><br /><br />Outlook for iPad and iPhone<sup>4</sup><br /><br />OWA for iOS<sup>3</sup><br /><br />Secure Islands IQProtector<sup>1</sup><br /><br />TITUS Mail|RMS 共用應用程式 <sup>1</sup>：文字、影像、pfile<br /><br />TITUS Docs：Pfile|
|**Android**|GigaTrust App for Android<br /><br />Office Online<sup>2</sup>|GigaTrust App for Android<br /><br />Foxit Reader<br /><br />RMS 共用應用程式 <sup>1</sup>|9Folders<sup>4</sup><br /><br />GigaTrust App for Android<sup>4</sup><br /><br />NitroDesk<sup>4</sup><br /><br />OWA for Android<sup>3</sup> <sup>6</sup><br /><br />Samsung Email (S3 和更新版本)<sup>6</sup><br /><br />Secure Islands IQProtector<sup>1</sup><br /><br />TITUS Classification for Mobile|RMS 共用應用程式 <sup>1</sup>：文字、影像、pfile|
|**OS X**|Office 2011 (僅適用於 AD RMS)<br /><br />Office 2016 for Mac<br /><br />Office Online<sup>2</sup>|Foxit Reader<br /><br />RMS 共用應用程式 <sup>1</sup>|Outlook 2011 (僅適用於 AD RMS)<br /><br />Outlook 2016 for Mac<br /><br />Outlook for Mac|RMS 共用應用程式 <sup>1</sup>：文字、影像、pfile|
|**Windows RT**|Office 2013 RT<br /><br />Office Online<sup>2</sup>|不支援|Outlook 2013 RT<br /><br />Windows 版郵件應用程式<br /><br />Windows Mail<sup>4</sup>|Siemens JT2Go：JT 檔案|
|**Windows Phone 8.1**|Office Mobile (僅適用於 AD RMS)|RMS 共用應用程式 <sup>1</sup>|Outlook Mobile<sup>4</sup>|RMS 共用應用程式 <sup>1</sup>：文字、影像、pfile|
|**Blackberry 10**|不支援|不支援|Blackberry 電子郵件 <sup>4</sup>|不支援|
<sup>1</sup> 支援檢視受保護的內容。

<sup>2</sup> 支援檢視 SharePoint Online、商務用 OneDrive 和 Outlook Web Access 中受保護的內容。

<sup>3</sup> 如果收件者的信箱在內部部署的 Exchange 中，並收到受保護的電子郵件，則只可以在豐富的電子郵件用戶端 (如 Outlook) 中開啟此內容。  不能從 Outlook Web Access 開啟此內容。

<sup>4</sup> 使用 Exchange ActiveSync IRM，必須由 Exchange 系統管理員啟用。 使用者可以檢視、回覆和全部回覆受保護的電子郵件訊息，但使用者本身無法保護新的電子郵件訊息。

如果收件者的信箱在內部部署的 Exchange 中，並收到來自其他使用 Exchange 的組織的受保護電子郵件，則只可以在豐富的電子郵件用戶端 (如 Outlook) 中開啟此內容。  不能從使用 Exchange Active Sync IRM 的裝置開啟此內容。

<sup>5</sup> 支援檢視和編輯受保護的文件。 如需詳細資訊，請參閱下列 Office 部落格文章：[Azure Rights Management 支援已適用 Office for iPad and iPhone](https://blogs.office.com/2015/07/22/azure-rights-management-support-comes-to-office-for-ipad-and-iphone-2/)

<sup>6</sup> 如需詳細資訊，請參閱下列 Office 部落格文章：[OWA for Android 目前可在選取的裝置上使用](http://blogs.office.com/2014/06/11/owa-for-android-now-available-on-select-devices/)

> [!TIP]
> 如需 Office 即將在不同平台推出的 RMS 支援的詳細資訊，請參閱下列 Office 部落格文章：[Office 和加密功能無所不在](http://blogs.office.com/2015/02/18/office-everywhere-encryption-everywhere/)

## <a name="BKMK_SupportedApplications"></a>支援 Azure RMS 的應用程式
下列應用程式原生支援 Azure RMS，這意味 RMS 使用 RMS API 來支援使用限制，藉此嚴密整合至這些應用程式中。 這些應用程式也稱為 RMS 創新：

-   來自下列套件的 **Microsoft Office 應用程式** (Word、Excel、PowerPoint 和 Outlook) 可使用 Azure RMS 保護內容：

    -   Office 365 ProPlus

    -   Office 365 企業版 E3

    -   Office 365 Enterprise E4

    -   Office 365 企業版 E5

    -   Office Professional Plus 2016

    -   Office Professional Plus 2013

    -   Office Professional Plus 2010

    其他版本的 Office (不包括 Office 2007) 可以使用受保護的內容。

    > [!NOTE]
    > Azure RMS 與 Office Professional Plus 2010 或 Office Professional 2010：
    > 
    > -   需要適用於 Windows 的 Rights Management 共用應用程式
    > -   不支援 Windows 10

-   **適用於 Windows 的 Rights Management 共用應用程式**

    如需有關適用於 Windows 之 Rights Management 共用應用程式的詳細資訊，請參閱下列資源：

    -   [Rights Management 共用應用程式系統管理員指南 (英文)](http://technet.microsoft.com/library/dn339003.aspx)

    -   [Rights Management 共用應用程式使用者指南 (英文)](http://technet.microsoft.com/library/dn339006.aspx)

-   **行動平台的 Rights Management 共用應用程式**

    如需有關行動平台之 Rights Management 共用應用程式的詳細資訊，請參閱下列資源：

    -   使用 [Microsoft Rights Management 頁面](http://go.microsoft.com/fwlink/?LinkId=303970)上的連結，下載相關的應用程式

    -   如果使用 Microsoft Intune 管理行動裝置，您可以將 [iOS 和 Android 裝置上的應用程式當作原則管理應用程式](HTTPs://technet.microsoft.com/library/dn878026.aspx) 來加以部署與設定。

    -   [行動平台的 Microsoft Rights Management 共用應用程式常見問題集](http://technet.microsoft.com/dn451248)

-   **支援 RMS API 的其他應用程式**：

    -   使用 RMS SDK 在內部撰寫的企業營運系統應用程式

    -   使用 RMS SDK 撰寫之軟體廠商的應用程式

    如需有關 SDK 的詳細資訊，請參閱＜[Microsoft Rights Management SDK](http://msdn.microsoft.com/library/hh552972%28v=vs.85%29.aspx)＞。

> [!IMPORTANT]
> Azure RMS 目前不支援下列應用程式：
> 
> -   Microsoft Office for Mac 2011
> -   Microsoft OneDrive for Business for SharePoint Server 2013
> -   XPS 檢視器
> 
> 此外，RMS 共用應用程式具有下列限制：
> 
> -   若為 Windows 電腦：需要 Windows 7 Service Pack 1 的最低版本

如需這些應用程式如何支援 Azure RMS 的詳細資訊，請參閱＜[應用程式如何支援 Azure Rights Management](../Topic/How_Applications_Support_Azure_Rights_Management.md)＞。

如需有關執行方式的詳細資訊，請參閱＜[設定 Azure Rights Management 的應用程式](../Topic/Configuring_Applications_for_Azure_Rights_Management.md)＞。

## <a name="BKMK_SupportedServers"></a>支援 Azure RMS 的內部部署伺服器
當您使用 Azure RMS 連接器時可搭配使用下列內部部署伺服器產品與 Azure RMS，其作為內部部署伺服器與 Azure RMS 之間的通訊介面 (轉送)。 此外，此設定需要您在 Active Directory 樹系與 Azure Active Directory 之間設定目錄同步。

-   **Exchange Server**：

    -   Exchange Server 2013

    -   Exchange Server 2010

-   **Office SharePoint Server**：

    -   Office SharePoint Server 2013

    -   Office SharePoint Server 2010

-   **執行 Windows Server 並使用檔案分類基礎結構 (FCI) 的檔案伺服器**：

    -   Windows Server 2012 R2

    -   Windows Server 2012

    > [!NOTE]
    > 因為執行 Windows Server 2008 R2 的檔案伺服器沒有內建的檔案管理工作動作可套用 RMS 保護，您在此情況下無法使用 RMS 連接器。 不過，若您設定自訂檔案管理工作來執行可執行檔或指令檔，而這些檔案可使用 Azure RMS 來保護檔案，則您可以在這些作業系統上使用檔案分類基礎結構和 Azure RMS。 例如，使用 [RMS 保護 Cmdlet](https://msdn.microsoft.com/library/azure/mt433195.aspx) 的 Windows PowerShell 指令碼。
    > 
    > 您也可以對執行較新版本 Windows Server 的伺服器使用這些 Cmdlet，好處是這些 Cmdlet 可以保護所有檔案類型。 RMS 連接器只保護 Office 檔案。 如需相關指示，請參閱[具有 Windows Server 檔案分類基礎結構 &#40;FCI&#41; 的 RMS 保護](../Topic/RMS_Protection_with_Windows_Server_File_Classification_Infrastructure__FCI_.md)。

RMS 連接器在 Windows Server 2012 R2、Windows Server 2012 和 Windows Server 2008 R2 上受到支援。

如需有關如何為這些內部部署伺服器設定 RMS 連接器的詳細資訊，請參閱＜[部署 Azure Rights Management 連接器](../Topic/Deploying_the_Azure_Rights_Management_Connector.md)＞。

## 請參閱
[開始使用 Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

