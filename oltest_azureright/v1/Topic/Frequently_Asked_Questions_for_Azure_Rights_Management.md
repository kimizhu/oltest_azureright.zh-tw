---
description: na
keywords: na
title: Frequently Asked Questions for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 71ce491f-41c1-4d15-9646-455a6eaa157d
---
# Azure Rights Management 常見問題集
Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] 的一些常見問題集，也稱為 Azure RMS：

## 部署 Azure RMS 需要及如何執行哪些工作？
首先，請檢查 [Azure Rights Management 的需求](../Topic/Requirements_for_Azure_Rights_Management.md)，其中包含雲端訂閱選項的相關資訊、如何使用內部部署伺服器和 Azure RMS、目前不支援的部署案例、哪些裝置和應用程式支援 Azure RMS，以及當您需要防火牆或 Proxy 伺服器的 IP 位址和網域名稱清單時可用的連結。 您也可能想要檢查 [開始使用 Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md) 一節的其他主題，對 [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] 如何協助保護您組織的資料、其如何使用應用程式、其與內部部署版本的 Active Directory Rights Management 的比較結果，及 [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] 的特定術語和縮寫的基本瞭解。

接著當您準備自行測試 Azure RMS，或為您的組織進行部署時，請使用 [Azure Rights Management 部署藍圖](../Topic/Azure_Rights_Management_Deployment_Roadmap.md)以取得步驟清單，其中有詳細資訊及作法指示的連結。

如果需要其他資訊、資源和支援選項，請參閱 [Azure Rights Management 的資訊與支援](../Topic/Information_and_Support_for_Azure_Rights_Management.md)。

## 我可以整合 Azure RMS 與我的內部部署伺服器嗎？
可以。 Azure RMS 可與您的內部部署伺服器整合，例如 Exchange Server、SharePoint 和 Windows 檔案伺服器。 若要這樣做，請使用 [Rights Management 連接器](https://technet.microsoft.com/library/dn375964.aspx)。 或者，如果您只對在 Windows Server 上使用檔案分類基礎結構 (FC) 感興趣，您可以使用 [RMS 保護 Cmdlet](https://technet.microsoft.com/library/mt601315%28v=ws.10%29.aspx)。 您也可以同步處理 Active Directory 網域控制站與 Azure AD 並在兩者間建立同盟，以為使用者獲得更順暢的驗證體驗，例如使用 [Azure AD Connect](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/)。

Azure RMS 會在必要時自動產生及管理 XrML 憑證，因此它不會使用內部部署 PKI。 如需 Azure RMS 如何使用憑證的詳細資訊，請參閱[什麼是 Azure Rights Management？](../Topic/What_is_Azure_Rights_Management_.md)主題的＜[Azure RMS 運作方式的逐步解說：第一次使用、內容保護、內容取用](../Topic/What_is_Azure_Rights_Management_.md#BKMK_Walthrough)＞一節。

## 我有 Exchange 的混合式部署，有部分使用者在 Exchange Online 上，而其他的使用者在 Exchange 和其他人在 Exchange Server 上—Azure RMS 支援這個情形嗎？
絕對支援，而且其優點在於，使用者將能夠順暢地跨兩個 Exchange 部署保護和取用受保護的電子郵件和附件。 如需此組態，請[啟用 Azure RMS](https://technet.microsoft.com/library/jj658941.aspx) 並[啟用 Exchange online 的 IRM](https://technet.microsoft.com/library/dn151475%28v=exchg.150%29.aspx)，然後為 Exchange Server [部署和設定 RMS 連接器](https://technet.microsoft.com/library/dn375964.aspx)。

## 如果我在生產中部署 Azure RMS，我的公司會不會在解決方案中遭到「鎖定」，或無法存取我們以 Azure RMS 保護之內容的風險？
不會，即使您決定不再使用 Azure RMS，您隨時都可以完全掌控您的資料，並且可以繼續存取它。 如需詳細資訊，請參閱[解除委任並停用 Azure Rights Management](../Topic/Decommissioning_and_Deactivating_Azure_Rights_Management.md)。

不過，在您解除委任 Azure RMS 部署之前，我們想要聽取您的意見並了解您為什麼這樣決定。 如果 Azure RMS 無法滿足您的商務需求，請在近期規畫新功能或有替代方案時洽詢我們。 請將電子郵件訊息傳送至 [AskIPTeam@Microsoft.com](mailto:askipteam@microsoft.com?subject=Planning%20to%20decommission%20Azure%20RMS)，我們會很樂意與您討論技術和商務需求。

## 我是否能控制哪些使用者可以使用 Azure RMS 來保護內容？
是，Azure RMS 具有適用於這種情況的使用者上線控制功能。 如需詳細資訊，請參閱[啟用 Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md) 主題中的[設定分階段部署的登入控制項](../Topic/Activating_Azure_Rights_Management.md#BKMK_OnboardingControls)一節。

## 我可以防止使用者與特定組織共用受保護的文件嗎？
Azure RMS 的其中一個最大優點是它支援企業對企業共同作業，您不必設定明確信任的每個夥伴組織，因為 Azure AD 會為您處理驗證程序。

沒有管理選項可供用來防止使用者安全地與特定組織共用文件。 例如，您要封鎖您不信任或在業務上與您競爭的組織。 防止 Azure RMS 將受保護的文件傳送給這些組織中的使用者將是徒勞無功的舉動，因為如此一來您的使用者將會以未受保護的狀態共用文件，這大概是您最不想要在此案例中看到的結果！ 舉例來說，這樣您將無法識別誰在與這些組織中的哪些使用者共用公司的機密文件，但如果文件 (或電子郵件) 有受到 Azure RMS 保護，您就能加以識別。

## 當我與公司外部人員共用受保護的文件時，如何讓該使用者通過驗證？
Azure RMS 一律使用 Azure Active Directory 帳戶和相關聯的電子郵件地址進行使用者驗證，讓系統管理員可以順暢進行企業對企業的共同作業。 如果其他組織使用 Azure 服務，使用者將會在 Azure Active Directory 擁有帳戶，即使這些帳戶已進行內部部署建立和管理並且同步處理至 Azure 亦然。  如果組織背後擁有 Office 365，此服務也會將 Azure Active Directory 用於使用者帳戶。  如果使用者的組織在 Azure 中沒有受管理的帳戶，使用者可以註冊 [個人版 RMS](https://technet.microsoft.com/library/dn592127.aspx)，它會利用使用者的帳戶為組織建立未受管理的 Azure 租用戶及目錄，讓此使用者可以通過 Azure RMS 的驗證。

這些帳戶的驗證方法可能會不同，取決於其他組織中的系統管理員對 Azure Active Directory 帳戶的設定方式。 比方說，他們可以使用為這些帳戶、多因素驗證 (MFA)、聯盟所建立的密碼，或是在 Active Directory 網域服務中建立並同步處理至 Azure Active Directory 的密碼。

## 我可以從公司外部將使用者新增至自訂範本嗎？
是。  建立使用者 (和系統管理員) 可以從應用程式中選取的自訂範本，可讓使用者快速並輕鬆地使用您指定的預先定義原則套用資訊保護。 範本中的其中一個設定是誰能夠存取內容，而且您可以從組織內指定使用者和群組，從組織外指定使用者。

若要指定您組織外部的使用者，請使用 [Azure Rights Management 的 Windows PowerShell 模組](https://technet.microsoft.com/library/jj585012.aspx)：

-   **使用權限定義物件來建立或更新範本**。    在您接著用來建立或更新範本的權限定義物件中，指定外部電子郵件地址及其權限。 使用 [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx) Cmdlet 來建立變數，然後將此變數提供給具備 [Add-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727075.aspx) Cmdlet (適用於新的範本) 或 [Set-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx) Cmdlet (用以修改現有的範本) 的 -RightsDefinition 參數，可指定權限定義物件。 不過，如果您要將這些使用者新增到現有的範本，您必須為範本中的現有群組 (而不只是外部使用者) 定義權限定義物件。

如需自訂範本的詳細資訊，請參閱[設定 Azure Rights Management 的自訂範本](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md)。

## Azure RMS 支援哪些裝置和檔案類型？
如需支援的裝置清單，請參閱 [Azure Rights Management 的需求](../Topic/Requirements_for_Azure_Rights_Management.md)主題中的 [支援 Azure RMS 的用戶端裝置](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedDevices)一節。 目前並非所有支援的裝置都能支援所有 RMS 功能，因此請務必另外查看同一主題中的[用戶端裝置功能](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_ClientCapabilities)表格。

Azure RMS 可支援所有檔案類型。 對於文字、影像、Microsoft Office (Word、Excel、PowerPoint) 檔案、.pdf 檔案及部分其他應用程式檔案類型，Azure RMS 提供了包含加密和增強權利 (權限) 的原生保護功能。 對於所有其他應用程式和檔案類型，一般保護提供檔案封裝及驗證來確認使用者是否獲得開啟檔案授權。

如需 Azure RMS 原生支援的副檔名清單，請參閱《[Rights Management 共用應用程式系統管理員指南](http://technet.microsoft.com/library/dn339003.aspx)》的[支援的檔案類型和副檔名](http://technet.microsoft.com/library/dn339003.aspx)一節。 使用會自動將一般保護套用到這些檔案的 RMS 共用應用程式可支援未列出的副檔名。

## 何時會支援從 AD RMS 移轉？
Azure RMS 最初並不支援從內部部署的 Rights Management (例如 AD RMS) 移轉。 但現在已支援。

如需詳細資訊，請參閱[從 AD RMS 移轉至 Azure Rights Management](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md)。

## 我們真的想要搭配使用 BYOK和 Azure RMS，聽說這樣無法和 Exchange Online 相容 — 有什麼好建議嗎？
請勿讓目前的限制延遲了您的 Azure RMS 部署。 如果您擁有 Exchange Online 並且想要使用整合您自己的金鑰 (BYOK)，建議您立即以 Microsoft 在其中產生並管理金鑰的預設金鑰管理模式來部署 Azure RMS。 如此一來，您就可以立即取得保護重要檔案和電子郵件的所有優點，並且可以在日後選擇移至 BYOK (例如，當 Exchange Online 可支援 BYOK 時)。

不過，如果您的公司原則要求您使用硬體安全性模組 (HSM)，這樣反而會封鎖您的 Azure RMS 部署，另一個選項是立即使用 BYOK 部署 Azure RMS，但是 RMS 對 Exchange 的功能會減少。 如需詳細資訊，請參閱[規劃及實作 Azure Rights Management 租用戶金鑰](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md)主題中的 [BYOK 定價和限制](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing)一節。

## 我正在尋找的功能似乎不是使用 SharePoint 受保護程式庫—有規劃對我的功能的支援嗎？
目前，SharePoint 使用 IRM 受保護程式庫支援 RMS 受保護文件，該程式庫不支援自訂範本、文件追蹤和一些其他功能。  如需詳細資訊，請展開＜[應用程式如何支援 Azure Rights Management](../Topic/How_Applications_Support_Azure_Rights_Management.md)＞主題的＜[SharePoint Online 和商務用 OneDrive：IRM 設定](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharePointOnline)＞一節。

如果您對尚不支援的特定功能有興趣，請務必留意 [RMS 小組部落格](http://blogs.technet.com/b/rms/)上的宣告。

## 如何在 SharePoint Online 中設定商務用 One Drive，讓使用者可以安全地與公司內外的人員共用其檔案？
根據預設，身為 Office 365 的系統管理員，您沒有進行此設定，但使用者已設定。

正如 SharePoint 網站系統管理員可啟用與設定其所擁有之 SharePoint 程式庫的 IRM，商務用 OneDrive 特別為使用者設計，以便啟用與設定本身商務用 OneDrive 程式庫的 IRM。  不過，透過使用 PowerShell，您即可為他們執行此作業。 如需相關指示，請展開[設定 Azure Rights Management 的應用程式](../Topic/Configuring_Applications_for_Azure_Rights_Management.md)文章中的[SharePoint Online 和商務用 OneDrive：IRM 設定](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_SharePointOnline)一節。

## 您是否具有成功部署 RMS 的任何秘訣或訣竅？
審視許多部署案例並傾聽我們的客戶、夥伴、顧問和支援工程師意見後，我們從經驗中可傳達的其中一個最大秘訣是：**設計和部署簡單適當的原則**。

由於 Azure RMS 支援與任何人安全共用，因此您可確保建構完善的資訊防護機制。 但請遵循適當的原則謹慎施行。 對許多組織而言，預防資料流失對企業最大的影響是，套用預設的適當原則範本來限制組織中人員的存取。 當然，您可視需要取得更精細的防護，如防止人員列印、編輯等等。但這些更精細的限制不適用於真正需要高層級安全性的文件，且不要只實作這些限制較多的原則一天，而是要將其視為階段性方案加以規劃。

## 哪些功能可以或不能與 Azure RMS 的不同訂閱搭配使用？
以支援 Azure RMS 的付費訂閱而言 (Office 365、Azure RMS Premium 和 Enterprise Mobility Suite)，支援的 RMS 功能有一些差別。 如需相關清單，請參閱 [Rights Management Services (RMS) 產品項目的比較](http://technet.microsoft.com/dn858608)。

支援 Azure RMS 的免費訂閱 (個人版 RMS) 支援取用已由 Azure RMS 所保護的內容。 如需詳細資訊，請參閱[個人版 RMS 和 Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md)。

## 我可以在哪裡取得有關免費 Azure RMS 訂閱 (個人版 RMS) 的技術資訊 - 例如，實際運作方式、如何掌控帳戶及不能使用哪些網域？
您可以在 [個人版 RMS 和 Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md) 主題中找到這些問題的答案。

## 我們要如何重新存取現在已離開組織的員工所保護的檔案？
使用 Azure RMS 的進階使用者功能，可以讓獲得授權的使用者擁有貴組織的 RMS 租用戶所授與之所有使用授權的完整擁有權。 此相同功能可在必要時讓獲得授權的服務編製索引並檢查檔案。

如需詳細資訊，請參閱[設定 Azure Rights Management 和探索服務或資料復原的進階使用者](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md)。

## Rights Management 可以防止擷取螢幕畫面嗎？
Rights Management 會阻止大多數常用的螢幕擷取畫面工具，這有助於避免意外或疏忽洩漏機密或敏感性資訊。 不過，使用者有許多方法可以分享螢幕上顯示的資料，擷取螢幕畫面只有其中一種方法而已。 例如，意圖分享顯示資訊的使用者可以利用其照相手機拍照、重新鍵入資料，或只是以口頭方式傳播給他人。

如這些範例所示，技術本身無法永遠阻止使用者分享他們不該分享的資料。 雖然 Rights Management 可利用授權和使用原則協助保護您的重要資料，但這套企業級權限管理解決方案應搭配其他控制使用。 例如，實作實體安全性，仔細篩選和監督獲得授權存取您的組織資料的人員，以及投入使用者教育，讓使用者瞭解哪些資料不應該分享。

## 哪邊可以找到法律、規範和 SLA 等方面的 Azure RMS 支援資訊？
Azure RMS 既支援其他服務，同時也仰賴其他服務。 如果您要尋找的資訊與 Azure RMS 有關，但與如何使用 Azure RMS 服務無關，請查看下列資源：

**法律和隱私權：**

-   Microsoft Azure 合約資訊：[Microsoft Azure 合約](http://azure.microsoft.com/support/legal/subscription-agreement/)

-   Microsoft Azure 隱私權資訊：[Microsoft Azure 隱私權聲明](http://azure.microsoft.com/support/legal/privacy-statement/)

**安全性、規範以及稽核：**

請參閱[什麼是 Azure Rights Management？](../Topic/What_is_Azure_Rights_Management_.md) 主題中的[安全性、規範和法規要求](../Topic/What_is_Azure_Rights_Management_.md#BKMK_RMScompliance)一節。 此外：

-   Azure RMS 的外部憑證：[Microsoft Azure 信任中心](http://azure.microsoft.com/support/trust-center/)

-   如需 FIPS 140 資訊：[FIPS 140 驗證](https://technet.microsoft.com/library/security/cc750357.aspx)

**服務等級協定：**

-   Azure RMS 的服務等級協定 (以選定的國家/地區列出)：[服務等級協定](http://microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&amp;DocumentTypeId=37)

-   Azure Active Directory 的服務等級協定：[服務等級協定](http://azure.microsoft.com/support/legal/sla/)

**文件：**

-   Azure Active Directory 文件網站：[Azure Active Directory](http://azure.microsoft.com/documentation/services/active-directory/)

-   Azure Active Directory 程式庫：[Azure Active Directory](http://msdn.microsoft.com/library/azure/jj673460.aspx)

-   Office 365 程式庫：[Office 365](http://technet.microsoft.com/library/dn127064%28v=office.14%29.aspx)

## 我的問題不在那裏怎麼辦？
使用 [Azure Rights Management 的資訊與支援](../Topic/Information_and_Support_for_Azure_Rights_Management.md)中所列的連結和資源。

此外，有針對使用者設計的常見問題集：

-   [適用於 Windows 的 Rights Management 共用應用程式的常見問題集](https://technet.microsoft.com/dn467883)

-   [行動和 Mac 平台的 Rights Management 共用應用程式常見問題集](https://technet.microsoft.com/dn451248)

-   [文件追蹤的常見問題集](http://go.microsoft.com/fwlink/?LinkId=523977)

此常見問題集頁面將會定期更新 [Microsoft Rights Management (RMS) 小組](http://blogs.technet.com/b/rms/)部落格的每月文件更新宣告中所列的新增部分。

> [!TIP]
> 您可以利用部落格上的[文件標籤](http://blogs.technet.com/b/rms/archive/tags/docs/)來尋找這些文件公告。

## 請參閱
[開始使用 Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

