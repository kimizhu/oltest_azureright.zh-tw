---
description: na
keywords: na
title: How Applications Support Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2cdc7bde-4044-4021-b887-11476f99afd9
---
# 應用程式如何支援 Azure Rights Management
使用下列資訊可協助您了解使用者應用程式 (例如 Office 應用程式、Word、Excel、PowerPoint 及 Outlook) 和服務 (例如 Exchange 和 SharePoint) 如何使用 Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] 來協助保護貴組織的資料：

-   [適用於 Windows 和行動平台的 RMS 共用應用程式](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_SharingAppIntro)

-   [Office 應用程式：Word、Excel、PowerPoint 及 Outlook](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_OfficeAppsIntro)

    -   [Exchange Online 和 Exchange Server](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_ExchangeIntro)

    -   [SharePoint Online 和 SharePoint Server](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_SharePointIntro)

-   [執行 Windows Server 並使用檔案分類基礎結構 (FCI) 的檔案伺服器](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_FCIIntro)

-   [其他支援 RMS API 的應用程式](../Topic/How_Applications_Support_Azure_Rights_Management.md#BKMK_APIAppsIntro)

> [!NOTE]
> 若要確認 [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS) 支援的應用程式和版本，請參閱 [Azure Rights Management 的需求](../Topic/Requirements_for_Azure_Rights_Management.md)。

在某些情況下，會根據您設定的原則自動套用資訊保護。 例如，SharePoint 文件庫、分類的檔案及 Exchange 傳輸規則就是這樣的情況。 在其他情況下，使用者則必須藉由選取範本或選取特定的選項，從他們的應用程式自行套用資訊保護。 例如，當使用者以電子郵件分享檔案，或對選取的使用者或組織外的使用者限制存取或使用以就地保護檔案時，就是這種情況。

範本可讓使用者 (和設定原則的系統管理員) 更容易套用正確的保護層級，以及對貴組織內部的人員限制存取。 雖然 [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] 隨附兩個預設範本，但是您可能會想要建立自訂範本以縮減必須指定個別選項的時間。 如需詳細資訊，請參閱[設定 Azure Rights Management 的自訂範本](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md)。

針對使用者必須自行套用資訊保護的情況，請務必提供他們如何及何時套用資訊保護的指示和指導。 指示應該要針對他們所使用的應用程式和版本及使用方式，而何時及如何套用資訊保護的指導應該要適用於您的業務。 如需詳細資訊，請參閱[協助使用者使用 Azure Rights Management 來保護檔案](../Topic/Helping_Users_to_Protect_Files_by_Using_Azure_Rights_Management.md)。

如需如何為 Azure RMS 設定這些應用程式的詳細資訊，請參閱[設定 Azure Rights Management 的應用程式](../Topic/Configuring_Applications_for_Azure_Rights_Management.md)。

> [!TIP]
> 如需使用 Azure RMS 之應用程式的範例和螢幕擷取畫面，請參閱[什麼是 Azure Rights Management？](../Topic/What_is_Azure_Rights_Management_.md)主題中的＜[Azure RMS 運作方式：系統管理員和使用者看到的內容](../Topic/What_is_Azure_Rights_Management_.md#BKMK_RMSpictures)＞一節。

## <a name="BKMK_SharingAppIntro"></a>適用於 Windows 和行動平台的 RMS 共用應用程式
RMS 共用應用程式是一個免費、可下載的應用程式，這是支援 Office 2010 的必要應用程式，也建議在 Windows 電腦、Mac 電腦和行動裝置上使用。 它的其中一個好處就是可以針對原本不支援 [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] 的應用程式和檔案套用一般保護，也就是說可以保護所有檔案。 如需不同保護層級的詳細資訊，請參閱《[Rights Management 共用應用程式系統管理員指南](http://technet.microsoft.com/library/dn339003.aspx)》中的＜[保護層級 – 原生和一般](http://technet.microsoft.com/library/dn339003.aspx)＞一節。

使用者使用 RMS 共用應用程式保護檔案時，可以同時追蹤他們所保護的文件，而且可以撤銷對檔案的存取權 (如有必要)。 使用[文件追蹤網站](http://go.microsoft.com/fwlink/?LinkId=529562)便可以這麼做。

對 Windows 電腦來說，RMS 共用應用程式會暗中與使用者已使用的應用程式整合並增強那些應用程式：

-   會安裝一個適用於 Word、Excel、PowerPoint 及 Outlook 的 Office 增益集。 這可在功能區上為使用者提供 [共用保護] 按鈕，這個按鈕會叫用一個易於使用的對話方塊，其中包含用於保護通過電子郵件傳送之檔案的最常用設定。 使用這個按鈕還可以快速存取文件追蹤網站。

-   一個新的檔案總管滑鼠右鍵選項。 這可為使用者提供 [就地保護] 選項，這個選項會叫用一個易於使用的對話方塊，其中包含用於保護儲存在磁碟上之檔案的最常用設定。

-   一個可開啟已受 [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] 保護之檔案的檢視器。 當沒有安裝任何其他可開啟受保護檔案的應用程式時，便會自動叫用這個檢視器。

-   可讓來自 Office 2010 套件的 Word、Excel、PowerPoint 及 Outlook 與 [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] 一起順暢運作的 Office 2010 後端設定。

雖然您可以使用 [Microsoft Rights Management 頁面](http://go.microsoft.com/fwlink/?LinkId=303970)來針對單一電腦下載及安裝適用於 Windows 的 RMS 共用應用程式，不過它也支援透過企業部署來進行無訊息安裝和自訂設定。 如需詳細資訊，請參閱下列資源：

-   [Rights Management 共用應用程式系統管理員指南 (英文)](http://technet.microsoft.com/library/dn339003.aspx)

-   [Rights Management 共用應用程式使用者指南 (英文)](http://technet.microsoft.com/library/dn339006.aspx)

適用於行動裝置的 RMS 共用應用程式支援最常用的行動裝置，例如 iPad 和 iPhone、Android、Windows Phone 及 Windows RT。 使用者可以從相關的市集下載這個應用程式，從 [Microsoft Rights Management 頁面](http://go.microsoft.com/fwlink/?LinkId=303970)即可取得這些相關連結。

## <a name="BKMK_OfficeAppsIntro"></a>Office 應用程式：Word、Excel、PowerPoint 及 Outlook
這些應用程式原本就使用資訊版權管理 (IRM) 支援 Rights Management，並可讓使用者套用保護至儲存的文件或要傳送的電子郵件訊息。 使用者可以套用範本或選擇自訂程度很高的設定來限制存取、權限及使用。 例如，使用者可以設定讓檔案僅供貴組織中的人員存取，或是控制檔案是否可供編輯、限制成唯讀或防止列印。 對於時間有限的檔案，可以設定一個讓檔案不能再被存取的到期時間 (由使用者直接設定或透過套用範本設定)。 Outlook 的使用者還可以選擇 [不可轉寄] 選項來協助防止資料外洩。

### <a name="BKMK_ExchangeIntro"></a>Exchange Online 和 Exchange Server
使用 Exchange Online 或 Exchange Server 時，您可以使用資訊版權管理 (IRM) 整合來提供其他資訊保護方案：

-   **Exchange ActiveSync IRM**：可讓行動裝置保護和使用受保護的電子郵件訊息。

-   適用於 **Outlook Web App** 的 RMS 支援：實作方式與 Outlook 用戶端類似，可讓使用者透過範本或指定個別選項來保護電子郵件訊息，而且使用者可以讀取和使用傳送給他們的受保護電子郵件訊息。

-   適用於 Outlook 用戶端的**保護規則**：這是系統管理員所設定，可將 RMS 範本自動套用至指定之收件者的電子郵件訊息。 例如，當內部電子郵件被傳送至您的法務部門時，只有法務部門的成員可以讀取該郵件且無法轉寄。 使用者會在傳送電子郵件訊息之前看到訊息已套用保護，並且根據預設，如果使用者覺得沒有必要套用保護，便可將保護移除。 電子郵件會先經過加密再傳送。 如需詳細資訊，請參閱 Exchange 文件庫中的 [Outlook 保護規則](http://technet.microsoft.com/library/dd638178%28v=exchg.150%29.aspx)和[建立 Outlook 保護規則](http://technet.microsoft.com/library/dd638196%28v=exchg.150%29.aspx)。

-   **傳輸規則**：這是系統管理員所設定，可根據寄件者、收件者、郵件主旨及內容之類的屬性，將 RMS 範本自動套用至電子郵件訊息。 這些規則在概念上與保護規則類似，但是無法讓使用者移除保護、可以套用至 Outlook Web Access 和行動裝置所傳送的電子郵件，並且從用戶端傳送電子郵件訊息之前不會予以加密。 如需詳細資訊，請參閱 Exchange 文件庫中的[建立傳輸保護規則](http://technet.microsoft.com/library/dd302432.aspx)。

-   **資料外洩防護 (DLP) 原則**：包含幾組條件，可篩選電子郵件訊息並採取動作來協助防止機密或敏感性內容 (例如個人資訊或信用卡資訊) 的資料外洩。 偵測到敏感性資料時可以使用原則提示，以根據電子郵件訊息中的資訊來警示使用者可能需要套用資訊保護。 如需詳細資訊，請參閱 Exchange 文件庫中的[資料外洩防護](http://technet.microsoft.com/library/jj150527%28v=exchg.150%29.aspx)。

-   **Office 365 郵件加密**：這會使用傳輸規則將加密的電子郵件傳送給貴公司外的人員，並且是在介面類似於 Outlook Web App 的瀏覽器中讀取電子郵件。 您可以在貴公司的加密電子郵件中自訂免責聲明文字和標頭文字，甚至是加入貴公司的標誌。 如需詳細資訊，請參閱 Office 網站上的 [Office 365 郵件加密](http://office.microsoft.com/o365-message-encryption-FX104179182.aspx)。

如果您使用的是 Exchange Server，則可透過部署 RMS 連接器將資訊保護功能與 [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] 搭配使用，RMS 連接器會負責您內部部署伺服器與 RMS 雲端服務之間的轉送。 如需詳細資訊，請參閱[部署 Azure Rights Management 連接器](../Topic/Deploying_the_Azure_Rights_Management_Connector.md)。

### <a name="BKMK_SharePointIntro"></a>SharePoint Online 和 SharePoint Server
使用 SharePoint Online 或 SharePoint Server 時，您可以使用資訊版權管理 (IRM) 整合，讓系統管理員能夠保護清單或文件庫，以便在使用者簽出文件時保護檔案，而只有獲授權的人員可以根據您指定的資訊保護原則來檢視和使用該檔案。 例如，檔案可能為唯讀、停用文字複製功能、不允許儲存本機複本以及不允許列印檔案。

清單和文件庫的資訊保護一律是由系統管理員套用，絕對不會由使用者套用。 而且，它是套用在該容器中所有文件的清單或文件庫層級，而不是套用在個別檔案。  如果您使用 SharePoint Online，使用者也可以套用 IRM 至其 OneDrive for Business 文件庫。

您必須先為 SharePoint 啟用 IRM 服務。 然後，您可以指定程式庫的資訊版權管理。 在 SharePoint Online 和 OneDrive for Business，使用者也可以為其 OneDrive for Business 文件庫指定資訊版權管理。 雖然您可以選取最符合可在範本中所指定設定的 SharePoint 組態設定，但是 SharePoint 不會使用權限原則範本。

如果您使用的是 SharePoint Server，則可透過部署 RMS 連接器將資訊保護功能與 [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] 搭配使用，RMS 連接器會負責您內部部署伺服器與 RMS 雲端服務之間的轉送。 如需詳細資訊，請參閱[部署 Azure Rights Management 連接器](../Topic/Deploying_the_Azure_Rights_Management_Connector.md)。

> [!NOTE]
> 目前，搭配使用 IRM 和 SharePoint 有一些限制：
> 
> -   您無法使用您在 Azure 傳統入口網站中管理的預設或自訂範本。
> -   受保護的 PDF 檔案不支援副檔名為 .PPDF 的檔案。 使用原生支援 RMS 的 PDF 閱讀程式時，支援副檔名為 .PDF 原本就受 RMS 保護的檔案。
> -   因為行動裝置上的 Office 尚未支援 RMS，這些裝置必須使用瀏覽器來檢視受 RMS 保護的檔案和唯讀檔案。

從 SharePoint 下載文件時，Azure RMS 就會對文件套用使用限制和資料加密，而不是在第一次於 SharePoint 建立文件或上載到文件庫時套用。 有關如何在下載前保護文件的資訊，請參閱 SharePoint 文件中的[商務用 OneDrive 和 SharePoint Online 中的資料加密](https://technet.microsoft.com/library/dn905447.aspx)。

如需搭配使用 Azure RMS 和 SharePoint的詳細資訊，請參閱下列 Office 部落格文章：[SharePoint 和 SharePoint Online 的資訊版權管理新功能](http://blogs.office.com/2012/11/09/whats-new-with-information-rights-management-in-sharepoint-and-sharepoint-online/)

## <a name="BKMK_FCIIntro"></a>執行 Windows Server 並使用檔案分類基礎結構 (FCI) 的檔案伺服器
設定 Windows Server 使用檔案分類基礎結構時，這項檔案伺服器資源管理員功能可以掃描本機檔案，並判斷它們是否包含敏感性資料。 符合這個準則的檔案會被標記系統管理員所定義的分類屬性。 接著，檔案分類基礎結構便可根據分類採取自動動作。 其中一個動作是使用 [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] 和資訊版權管理連接器 (又稱為 RMS 連接器) 部署來套用資訊保護。 Azure RMS 就會自動保護 Office 檔案。

若要保護所有檔案類型，請勿使用 RMS 連接器，而是改成從 [RMS 保護工具](https://www.microsoft.com/en-us/download/details.aspx?id=47256) 使用 Cmdlet 執行 Windows PowerShell 指令碼。

分類原則既可完全設定又極具延伸性，可讓您防止可能由未獲授權和已獲授權的使用者引起的資料外洩。 它甚至可以協助降低由網路系統管理員引起的資料外洩風險，因為您可以設定不需要這些系統管理員存取檔案的原則。

如需部署和配置 Office 檔案之 RMS 連接器的指示，請參閱[部署 Azure Rights Management 連接器](../Topic/Deploying_the_Azure_Rights_Management_Connector.md)。

如需對所有檔案類型使用 Windows PowerShell 指令碼的指示，請參閱[具有 Windows Server 檔案分類基礎結構 &#40;FCI&#41; 的 RMS 保護](../Topic/RMS_Protection_with_Windows_Server_File_Classification_Infrastructure__FCI_.md)。

## <a name="BKMK_APIAppsIntro"></a>其他支援 RMS API 的應用程式
藉由使用 RMS SDK，您的內部開發人員便可以撰寫原本就支援的 [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] 的企業營運系統應用程式。 資訊保護與這些應用程式的整合方式取決於其撰寫方式。 例如，可能會自動套用整合而只需極少的使用者互動，或是在進行較多自訂的情況下，可能會提示使用者設定一些將資訊保護套用至檔案的設定。 如需有關 SDK 的詳細資訊，請參閱＜[Microsoft Rights Management SDK](http://msdn.microsoft.com/library/hh552972%28v=vs.85%29.aspx)＞。

同樣地，許多軟體廠商也提供應用程式來提供資訊保護解決方案，亦稱為企業版權管理 (ERM) 產品。 其中一個常見的範例就是針對特定平台支援 [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] 的 PDF 閱讀程式。 您可以使用 [Azure Rights Management 的需求](../Topic/Requirements_for_Azure_Rights_Management.md) 主題中的＜[用戶端裝置功能](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_ClientCapabilities)＞一節的表格，識別支援 RMS 的應用程式 (啟用 RMS 的應用程式)，然後再透過網路搜尋購買或下載應用程式。

> [!TIP]
> 針對新發行的應用程式，請查看 [Azure Rights Management 的資訊與支援](../Topic/Information_and_Support_for_Azure_Rights_Management.md)中所列的 RMS 社群管道。

## 請參閱
[開始使用 Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

