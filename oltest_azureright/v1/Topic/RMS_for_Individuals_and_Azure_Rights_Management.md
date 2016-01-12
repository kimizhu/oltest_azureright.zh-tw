---
description: na
keywords: na
title: RMS for Individuals and Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2efcb440-fefd-45e9-872b-f471573aadf2
---
# 個人版 RMS 和 Azure Rights Management
個人版 RMS 是免費自助訂閱，適用於組織中已接收受 Microsoft Azure Rights Management (Azure RMS) 保護之敏感檔案的使用者，但是他們無法通過驗證，因為其 IT 部門沒有為他們在 Azure 中管理帳戶。 例如，IT 部門不會有 Office 365 或使用 Azure 服務。

這些使用者可申請免費的工作或學校帳戶來使用 Azure RMS，並下載和安裝 Rights Management 共用應用程式。 如此一來，這些使用者現在可以進行驗證，來證明他們就是接收受保護檔案的人員，然後讀取電腦或行動裝置上的受保護檔案。

在 Windows 電腦上使用 Rights Management 共用應用程式時，這些使用者也能就地保護檔案或以電子郵件將受保護檔案傳送給其組織內部或外部的人員。 如果他們傳送電子郵件的收件者位於沒有在 Azure 中管理使用者帳戶的組織，他們亦可於申請個人版 RMS 帳戶後讀取受保護的電子郵件附件。

> [!IMPORTANT]
> 此免費訂閱可確保授權的人員可一律讀取受保護的檔案。 目前，您也可以使用此免費訂閱保護文件和建立新的受保護電子郵件訊息，但撰寫新的受保護內容則僅供試用，並且未來可能會將其移除。 如需詳細資訊和使用個人版 RMS 來保護內容的任何變更，請參閱 [Microsoft Rights Management 服務條款](https://portal.aadrm.com/Legal/Service)。

如需使用免費 Rights Management 共用應用程式來保護檔案的詳細資訊，請參閱＜[Rights Management 共用應用程式使用者指南](http://technet.microsoft.com/library/dn339006.aspx)＞。

個人版 RMS 是 Azure Active Directory 支援的自助註冊範例。 如需有關其運作方式的詳細資訊，請參閱 Microsoft Azure 文件中的[何謂 Azure 的自助註冊？](https://azure.microsoft.com/documentation/articles/active-directory-self-service-signup/)。 使用下列各區段取得專屬於個人版 RMS 的詳細資訊：

-   [使用者如何申請個人版 RMS](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md#BKMK_SignUp)

    -   [技術概觀](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md#BKMK_TechnicalOverview)

-   [系統管理員如何控制個人版 RMS 建立的帳戶](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md#BKMK_TakeControlofAccounts)

-   [如何找出您的使用者是否已註冊個人版 RMS](#BKMK_Detect)

## <a name="BKMK_SignUp"></a>使用者如何申請個人版 RMS
若要註冊此免費帳戶，請造訪 [Microsoft Rights Management 頁面](https://portal.aadrm.com/)來申請註冊，並提供工作或學校電子郵件地址。 您將會被導向至這個註冊頁面的最常見方式是，您收到包含註冊方式說明之受保護附件的電子郵件訊息。 您會收到 Microsoft 的電子郵件回應，然後即可輸入詳細資料建立您的帳戶以完成註冊程序。 當您從 Microsoft 取得電子郵件確認時，此最終電子郵件訊息會傳送至一個頁面，您可以在其中下載不同裝置之共用應用程式，以及使用者指南的連結。

#### 若要申請個人版 RMS

1.  使用 Windows 或 Mac 電腦時，請移至 [Microsoft Rights Management 頁面](https://portal.aadrm.com)。

2.  鍵入您用於組織的電子郵件地址，例如 **janetm@contoso.com** 或 **p.dover@fabrikam.com**。

    > [!IMPORTANT]
    > 不支援個人電子郵件帳戶，因此請勿輸入 Microsoft 帳戶 (先前稱為 Microsoft Live ID 帳戶)，或您在家中可能使用的網際網路提供者的其他個人帳戶。

3.  按一下 [開始使用]。

    Microsoft 會使用您的電子郵件地址來檢查您的組織是否已具有[包含 Azure RMS 的付費定用帳戶](https://technet.microsoft.com/library/dn655136.aspx)。 如果是這種情況，您就不需要個人版 RMS，即可立即登入並取消個人版 RMS 的自助註冊。 如果找不到 Azure RMS 的付費訂用帳戶，您將會繼續進行下一個步驟。

4.  等候確認電子郵件訊息傳送至您所提供的位址。 它將來自 Microsoft (DoNotReply@microsoft.com) 且主旨為 **Microsoft RMS**。

5.  收到電子郵件時，請按一下指示中的連結來完成申請程序。

6.  此連結會將您帶到新的 [Microsoft Rights Management] 頁面，可讓您在頁面中提供您帳戶的詳細資料。 輸入您的名字和姓氏、輸入並確認您選擇的密碼、從下拉式清單選取您的國家/地區 (如果為列出您的國家/地區，則選取最接近的國家/地區)，然後按一下 [建立]。

7.  等候來自 Microsoft 的另一則電子郵件訊息，該訊息現在會確認您的帳戶已準備好使用。

8.  接收電子郵件時，請按一下連結登入並詳閱指示以下載和安裝共用應用程式，或按一下 [說明] 連結來閱讀共用應用程式使用者指南。

現在已建立您的帳戶，您可以準備好開始保護檔案和讀取其他人已保護的檔案。 系統提示您登入以保護或讀取受保護檔案時，請輸入您用來建立個人版 RMS 帳戶的電子郵件地址和密碼。

### <a name="BKMK_TechnicalOverview"></a>技術概觀
個人版 RMS 會使用自助式註冊程序，其他使用 Microsoft 雲端架構技術驗證使用者的服務也會使用此程序。

當使用者註冊個人版 RMS 且其組織沒有 Office 365 訂閱或 Azure 訂閱，使得 Azure 中沒有目錄可驗證使用者時，便會在背景啟用下列程序：

1.  當組織的第一個使用者要求個人版 RMS 訂閱時，會檢查其電子郵件地址中提供的網域名稱，查看其是否已與 Azure 租用戶相關聯。 如果沒有任何現有的租用戶，會自動為組織建立包含第一個使用者之帳戶的新租用戶與 Azure 目錄。 與 Azure 的付費訂用帳戶不同，第一個帳戶不是全域系統管理員，而是標準使用者。 新帳戶使用的是使用者提供的電子郵件地址及密碼。

    > [!NOTE]
    > 有些網域名稱無法用來建立目錄，因此無法用於個人版 RMS。 可從此「JavaScript 物件標記法」檔案檢視封鎖的網域名稱清單：[http://portal.aadrm.com/content/blocked_domains.json](http://portal.aadrm.com/content/blocked_domains.json)

    如果找到現有的租用戶，系統會檢查它以查看是否已經有 Azure RMS 的訂用帳戶。 找不到訂用帳戶時，可以新增免費個人版 RMS 訂用帳戶。

2.  此個人版 RMS 訂用帳戶可授與組織。 使用者現在可由 Azure 驗證，然後可以保護檔案，並讀取其他人已保護的檔案。 若要保護和讀取受保護檔案，使用者必須具有已啟用 RMS 的應用程式，例如安裝免費的 [Rights Management 共用應用程式](https://technet.microsoft.com/library/dn919648.aspx)。

3.  當相同組織的第二個使用者要求個人版 RMS 訂閱時，可使用組織的個人版 RMS 訂閱，將新使用者帳戶新增至先前建立的 Azure 目錄。 第二個使用者可執行第一名使用者可執行的每個動作 (保護檔案和讀取受保護檔案)，此外，這兩名使用者現在可安全且更輕易地共同作業，因為他們可將預設範本快速套用至檔案，對其組織之 Azure 目錄的帳戶存取設定限制。

4.  相同組織的使用者後續可遵循相同的模式，在新使用者登入時將使用者帳戶新增至組織的 Azure 目錄。 新增至目錄的帳戶愈多，就有愈多使用者可與同事和合作夥伴安全地共同作業，並更輕易地防止未經授權 (沒有存取權) 的人員讀取他們的檔案。

在整個程序中，組織完全無需付費，IT 部門也無需執行任何工作。 不過，IT 部門可選擇執行下列其中一項作業：

-   **管理帳戶及登入程序**：IT 系統管理員可取得在 Azure 中自動建立之目錄與帳戶的擁有權。 他們可接著實作目錄整合方案 (例如密碼同步和單一登入) 來管理帳戶。 或者，他們也可防止使用者建立帳戶或註冊個人版 RMS。

    如需詳細資訊，請參閱下節：[系統管理員如何控制個人版 RMS 建立的帳戶](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md#BKMK_TakeControlofAccounts)。

-   **管理 Rights Management**：IT 系統管理員可將組織的個人版 RMS 訂閱轉換為包含 Azure Rights Management 的付費訂閱。 當他們這麼做時，會保留現有的 Azure 目錄和帳戶，供仍在使用個人版 RMS 的現有使用者進行無縫轉換。 仍將遵循相同的原則保護其先前保護的任何檔案，且其授予檔案使用權限的人員仍可以相同的方式使用檔案。

    採取此類行動時，您的的組織可將 Rights Management 整合至其工作流程、服務和資料存放區而從中受益。 此外，您現在可管理 Rights Management，因為您擁有您組織 Azure Rights Management 租用戶金鑰的控制權。 您現在可執行下列動作：

    -   設定 Exchange 和 SharePoint 以支援 Azure Rights Management，即使它們正在執行內部部署也是如此。 Exchange 和 SharePoint 原生支援線上服務，並受內部部署伺服器的連接器支援。 如需詳細資訊，請參閱下列內容：

        -   ＜[設定 Azure Rights Management 的應用程式](../Topic/Configuring_Applications_for_Azure_Rights_Management.md)＞主題中的＜[Office 365：用戶端和線上服務的設定](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_O365)＞的 Exchange Online 和 SharePoint Online 一節

        -   [部署 Azure Rights Management 連接器](../Topic/Deploying_the_Azure_Rights_Management_Connector.md)

    -   在公司擁有的資料上執行 e-discovery，必要時解密使用 Rights Management 所保護的檔案。 如需詳細資訊，請參閱[設定 Azure Rights Management 和探索服務或資料復原的進階使用者](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md)。

    -   記錄組織中所使用 Rights Management 的所有活動。 這是極強大的功能，因為您不僅可監視正在保護哪些檔案，及監視正在成功存取那些受保護檔案的人員，亦可識別未授權人員正在嘗試存取受保護檔案的可疑行為。 如需詳細資訊，請參閱[記錄和分析 Azure Rights Management 使用情況](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md)。

    -   如果您的 [Azure RMS 訂用帳戶](https://technet.microsoft.com/dn858608)支援這些功能，請提供使用者此功能以追蹤及撤銷其受保護文件。 如需詳細資訊，請參閱 [RMS 共用應用程式使用者指南](https://technet.microsoft.com/library/dn339006.aspx)中的[追蹤及撤銷您的檔案](https://technet.microsoft.com/library/dn986611.aspx)。

    -   實作「整合您自己的金鑰方案 (BYOK)」，根據您的 IT 原則，在內部部署中產生 Azure Rights Management 的租用戶金鑰，並使用「硬體安全模組 (HSM)」安全地傳輸到 Microsoft。 如需詳細資訊，請參閱[規劃及實作 Azure Rights Management 租用戶金鑰](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md)。

## <a name="BKMK_TakeControlofAccounts"></a>系統管理員如何控制個人版 RMS 建立的帳戶
如果您不想將組織的個人版 RMS 訂閱轉換成付費訂閱，您仍可使用下列方法，控制您組織所建立之 Azure 目錄中的使用者帳戶：

-   為 Azure Active Directory 和 Active Directory 網域服務基礎結構實作目錄整合方案。 您可同步帳戶和密碼，讓該使用者不必建立新帳戶來使用 Rights Management，且您的內部部署密碼原則將套用至新 Azure 使用者帳戶。 您也可同步密碼，讓使用者不必記憶不同的密碼來使用 Rights Management。

-   您可防止使用者註冊並搭配使用 Azure Rights Management 與個人版 RMS 訂用帳戶。 這麼做在大多數情況下有一些好處，因為使用者將共用沒有保護的檔案 (可能讓您的公司處於風險中)，或將使用其他檔案保護機制，IT 部門將無法運用這種機制存取資料。 不過，若要防止使用者註冊並使用個人版 RMS，請在 Azure 中取得組織之目錄的擁有權後執行下列其中一個動作：

    -   防止所有使用者註冊自助訂用帳戶，其中包括個人版 RMS。  您目前無法設定此服務。此設定會套用至所有使用自助程序的 Azure 訂用帳戶。 若要進行此動作，請將 **AllowAdHocSubscriptions** 參數設為 false 加上來自 Azure Active Directory 之 Windows PowerShell 模組的 [Set-MsolCompanySettings](http://technet.microsoft.com/library/dn194127.aspx)。 例如：**Set-MsolCompanySettings -AllowAdHocSubscriptions $false**

    -   防止使用者在 Azure 建立新帳戶，代表只有已經在 Azure 擁有帳戶的使用者才能註冊包含個人版 RMS 的自助訂用帳戶。  若要進行此動作，請將 **AllowEmailVerifiedUsers** 參數設為 false 加上來自 Azure Active Directory 之 Windows PowerShell 模組的 [Set-MsolCompanySettings](http://technet.microsoft.com/library/dn194127.aspx)。 例如：**Set-MsolCompanySettings -AllowEmailVerifiedUsers $false -AllowAdHocSubscriptions $true**

    -   同步您的 Active Directory 網域服務基礎結構與 Azure Active Directory。 此動作可防止使用者在註冊個人版 RMS 等自助訂用帳戶時建立新帳戶，且您可刪除或停用先前在 Azure 目錄中建立的帳戶。

若要控制 Azure 目錄中的使用者帳戶，或防止使用者註冊個人版 RMS，您必須擁有 Azure 訂閱並擁有目錄。 如果您還沒有 Azure 訂用帳戶，您可以免費取得一個。 若在自助程序期間為您自動建立目錄，請取得用來建立網域的網域擁有權。 如果您已擁有在 Azure 中的目錄，但使用者指定您在組織中使用的新網域，請將該網域合併到現有的目錄中。 如需詳細資訊，請參閱[何謂 Azure 的自助註冊？](https://azure.microsoft.com/documentation/articles/active-directory-self-service-signup/)中的指示

## <a name="BKMK_Detect"></a>如何找出您的使用者是否已註冊個人版 RMS
身為系統管理員，您如何得知使用者是否已申請個人版 RMS？ 您可使用下列任一方法或一組方法：

-   詢問使用者如何保護高度機密檔案，特別是在與組織外部的其他人共同作業時。

-   當您在組織中具有 Azure 訂用帳戶時，請使用 [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx) 指令程式，並查看 **RIGHTSMANAGEMENT_ADHOC** 是否做為其中一個訂用帳戶傳回。 如果是，這會是授與組織的個人版 RMS 訂閱，提供使用者有效單位的集區以方便使用自助式註冊程序。

-   使用系統管理方案 (例如 System Center Configuration Manager) 來清查已安裝的軟體和使用中的軟體。 Rights Management 共用應用程式會藉由使用 **ipviewer.exe** 程式來執行，您可以免費[下載及安裝應用程式](http://go.microsoft.com/fwlink/?LinkId=303970)，以便識別後續將此應用程式用於軟體清查時的其他相關特性。

-   檢查 Rights Management 共用應用程式建立的副檔名。 .pfile 和 .ppdf 副檔名是最明顯的例子，但當它們由 Rights Management 原生保護時，有其他檔案可變更其副檔名。 如需詳細資訊，請參閱《[Rights Management 共用應用程式系統管理員指南](http://technet.microsoft.com/library/dn339003.aspx)》的＜[支援的檔案類型和副檔名](http://technet.microsoft.com/library/dn339003.aspx)＞一節。

## 請參閱
[開始使用 Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

