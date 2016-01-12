---
description: na
keywords: na
title: Configuring Custom Templates for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1775d8d0-9a59-42c8-914f-ce285b71ac1c
---
# 設定 Azure Rights Management 的自訂範本
在您啟用 Azure Rights Managementt (Azure RMS) 之後，使用者自動能夠使用兩個預設範本，讓他們可以輕鬆將原則套用至敏感性檔案，以限制僅供貴組織內已獲授權的使用者存取。 這兩個範本具有下列權限原則限制：

-   受保護內容的唯讀檢視

    -   顯示名稱：**&lt;organization name&gt; - 僅限機密檢視**

    -   特定權限：檢視內容

-   受保護內容的讀取或修改權限

    -   顯示名稱：**&lt;organization name&gt; - 機密**

    -   特定權限：檢視內容、儲存檔案、編輯內容、檢視指派的權限、允許巨集、轉寄、回覆、全部回覆

此外，[RMS 共用應用程式](http://technet.microsoft.com/library/dn339006.aspx)可讓使用者定義自己的權限集。 並且，在 Outlook 用戶端和 Outlook Web Access，使用者還可以針對電子郵件訊息選取 [不可轉寄] 選項。

對許多組織來說，預設範本可能就已經夠用。 但是，如果您想要建立自己的自訂權限原則範本，您也可以那麼做。 建立自訂範本的原因包括下列各項：

-   您想要一個可將權限授與組織中部分使用者而非全部使用者的範本。

-   您希望只有部分使用者能夠從應用程式中看到和選取範本 (部門範本)，而不是組織中所有使用者都能看到和選取範本。

-   您想要為範本定義自訂權限，例如「檢視」或「編輯」，但不要「複製」和「列印」。

-   您想要在範本中設定額外選項，包括到期日和是否可以在沒有網際網路連線的情況下存取內容。

若要讓使用者能夠選取包含這類設定的自訂範本，您必須先建立自訂範本、設定它，然後發佈它。

使用下列小節可協助您設定及使用自訂範本：

-   [如何建立、設定及發佈自訂範本](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_HowToConfigureCustomTemplates)

-   [如何複製範本](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_HowToCopyTemplates)

-   [如何移除 (封存) 範本](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_HowToArchiveTemplates)

-   [重新整理使用者的範本](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_RefreshingTemplates)

-   [Windows PowerShell 參考](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_PowerShellTemplates)

## <a name="BKMK_HowToConfigureCustomTemplates"></a>如何建立、設定及發佈自訂範本
您可以在 Azure 傳統入口網站中建立和管理自訂範本。 您可以直接從 Azure 傳統入口網站執行這項作業，或是登入 Office 365 系統管理中心並選擇 Rights Management 的 [進階功能]，這會將您重新導向到 Azure 傳統入口網站。

使用下列程序可建立、設定及發佈 Rights Management 的自訂範本。

#### 建立自訂範本

1.  依據您登入的是 Office 365 系統管理中心或是 Azure 傳統入口網站，執行下列其中一個動作：

    -   從 [Office 365 系統管理中心](https://portal.office.com/)：

        1.  按一下左窗格中的 [服務設定]。

        2.  從 [服務設定] 頁面中，按一下 [Rights Management]。

        3.  在 [保護您的資訊] 區段中，按一下 [管理]。

        4.  在 [Rights Management] 區段中，按一下 [進階功能]。

            > [!NOTE]
            > 如果您尚未啟用 Rights Management，請先按一下 [啟用]，然後確認您的動作。 如需詳細資訊，請參閱[啟用 Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md)。
            > 
            > 如果您之前沒有按一下 [進階功能]，則在 Rights Management 啟用之後，請依照畫面指示取得存取 Azure 傳統入口網站所需的免費 Azure 訂閱。

            按一下 [進階功能] 會載入 Azure 傳統入口網站，您可在此為您組織的 Azure Active Directory 管理 **RIGHTS MANAGEMENT**。

    -   登入 [Azure 傳統入口網站](http://go.microsoft.com/fwlink/p/?LinkID=275081)：

        1.  在左窗格中，按一下 **[ACTIVE DIRECTORY]**。

        2.  從 **[active directory]** 頁面中，按一下 **[RIGHTS MANAGEMENT]**。

        3.  為 Rights Management 選取要管理的目錄。

        4.  如果您尚未啟用 Rights Management，請按一下 [啟用]，然後確認您的動作。

            > [!NOTE]
            > 如需詳細資訊，請參閱[啟用 Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md)。

2.  建立新的範本：

    -   在 Azure 傳統入口網站中，從 [開始使用 Rights Management] 快速入門頁面，按一下 [建立新的權限原則範本]。

        如果在遵循 Office 365 的指示後未立即看到此頁面，請使用上述的 Azure 傳統入口網站導覽指示。

3.  在 [新增權限原則範本] 頁面上，選擇輸入使用者將看見的範本名稱和描述時要使用的語言 (您可以稍後新增其他語言)。 接著，輸入一個唯一的名稱和描述，然後按一下 [完成] 按鈕。

從 [開始使用 Rights Management] 快速入門頁面，現在按一下 [管理您的權限原則範本]。 您將會看見新建立的範本已新增至範本清單中，其狀態為 [已封存]。 在這個階段，範本已建立但尚未設定，使用者無法看見這個範本。

#### 設定及發佈自訂範本

1.  在 Azure 傳統入口網站的 [範本] 頁面中，選取您新建立的範本。

2.  從 [已新增您的範本] 快速入門頁面，從步驟 1 按一下 [開始使用]、[設定使用者和群組的權限]，然後按一下 [立即開始使用] 或 [新增]，接著選取將對新範本所保護的內容具有使用權限的使用者和群組。

    > [!NOTE]
    > 您所選取的使用者或群組必須有電子郵件地址。 在生產環境中，幾乎一律是這樣的情況，但是在簡單的測試環境中，您可能需要為使用者帳戶或群組新增電子郵件地址。

    最佳做法是選取群組而非使用者，這樣可簡化範本的管理。 如果您有 Active Directory 內部部署且正在同步處理至 Azure AD，您可以使用屬於安全性群組或通訊群組之已啟用郵件功能的群組。 不過，如果您想要將權限授與組織中的所有使用者，則更有效率的方式是複製其中一個預設範本，而不是指定多個群組。 如需詳細資訊，請參閱本主題中的[如何複製範本](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_HowToCopyTemplates)一節。

    > [!TIP]
    > 您稍後可以使用[適用於 Azure Rights Management 的 Windows PowerShell 模組](https://technet.microsoft.com/library/jj585012.aspx)並使用下列其中一種方法，將組織外部的使用者新增到範本：
    > 
    > -   **使用權限定義物件來更新範本**：  在您接著用來更新範本的權限定義物件中，指定外部電子郵件地址及其權限。 使用 [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx) Cmdlet 來建立變數，然後將此變數提供給具備 [Set-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx) Cmdlet (用以修改現有的範本) 的 -RightsDefinition 參數，即可指定權限定義物件。 不過，如果您要將這些使用者新增到現有的範本，您也必須為範本中的現有群組 (而不只是新的、外部使用者) 定義權限定義物件。
    > -   **匯出、編輯、匯入更新後的範本：**使用 [Export-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx) Cmdlet，將範本匯出到您可以編輯的檔案，以將這些使用者的外部電子郵件地址及其權限新增至現有的群組和權限。 然後使用 [Import-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx) Cmdlet 將此變更匯回到 Azure RMS 中。

3.  按 [下一步] 按鈕，然後將其中一個列出的權限指派給您所選取的使用者和群組。

    如需有關每個權限 (以及自訂權限) 的詳細資訊，請遵循顯示的說明。[設定 Azure Rights Management 的使用權限](../Topic/Configuring_Usage_Rights_for_Azure_Rights_Management.md) 中也會提供更詳細的資訊。 不過，支援 RMS 的應用程式在實作這些權限時可能使用不同的方式。 參考其文件，然後運用使用者用來檢查行為的應用程式執行您自己的測試，再部署使用者的範本。 若只要讓系統管理員看到此範本來執行這項測試，請將這個範本設定為部門範本 (步驟 6)。

4.  如果您選取了 [自訂]，請按 [下一步] 按鈕，然後選取那些自訂權限。

    雖然您可以使用可用的個別權限的任意組合，但在某些應用程式中，有些權限可能會與其他個別權限相依。 如果是這種情況，將會自動為您選取相依的權限。

    > [!TIP]
    > 考慮新增 [複製和解壓縮內容] 權限，並將此權限授予選取的系統管理員，或負責資訊還原的其他角色的個人。 授予此權限可讓他們依需要移除保護 (對在使用此範本時會受到保護的檔案和電子郵件)。 此功能可在範本層級移除保護，比使用超級使用者功能更能提供精確的控制。

5.  按一下 [完成] 按鈕。

6.  當使用者在應用程式中查看範本清單時，如果您只希望部分使用者看到範本：按一下 [範圍] 將此範本設定為部門範本，再按一下 [立即開始使用]。 否則，請移至步驟 9。

    部門範本的相關資訊：根據預設，Azure 目錄中的所有使用者都會看到所有已發佈的範本，他們接著可以從應用程式選取它們來保護其內容。 如果您只想要特定的使用者看到某些已發佈的範本，您必須針對這些使用者設定範本的範圍。 然後，只有這些使用者可以選取這些範本。 未指定的其他使用者看不到範本，因此無法加以選取。 這項技術可讓使用者更輕鬆地選擇正確的範本，尤其是當您建立專供特定的群組或部門使用的範本時。 使用者隨後只會看到針對他們所設計的範本。

    例如，您已為人力資源部建立範本，並將唯讀權限套用至財務部的成員。 如此一來，只有人力資源部的成員可在使用版權管理共用應用程式時套用此範本，因為您已針對具備電子郵件功能，且名為 HumanResources 的群組限制範本的範圍。 然後，只有此群組的成員可看到和套用這個範本。

7.  在 [範本可見性] 頁面上選取使用者和群組，讓他們可以從啟用 RMS 的應用程式中看見和選取範本。 如前所述，最佳的作法是使用群組而不是使用者，且您選取的群組或使用者必須擁有電子郵件地址。

8.  按 [下一步] 按鈕，並決定是否需要為部門範本設定應用程式相容性。 如果需要，請按一下 [應用程式相容性]，選取核取方塊，然後按一下 [完成]。

    為什麼您可能需要設定應用程式相容性？ 並非所有應用程式都可以支援部門範本。 若要這樣做，應用程式必須先通過 RMS 服務驗證才能下載範本。 如果未發生驗證程序，則預設不會下載任何部門範本。 您可以覆寫此行為，方法是指定應該下載所有部門範本，或設定應用程式相容性並選取 [當應用程式不支援使用者身分識別時，向所有使用者顯示這個範本] 核取方塊。

    例如，如果您未在人力資源部範例中設定部門範本的應用程式相容性，則在使用 RMS 共用應用程式時，只有人力資源部的使用者會看到部門範本，但所有使用者在從 Exchange Server 2013 使用 Outlook Web Access (OWA) 時都看不到部門範本，因為 Exchange OWA 及 Exchange ActiveSync 目前不支援部門範本。 如果您設定應用程式相容性來覆寫此預設行為，則在使用 RMS 共用應用程式時，只有人力資源部的使用者會看到部門範本，但所有使用者在使用 Outlook Web Access (OWA) 時都會看到部門範本。 如果使用者使用 OWA 或從 Exchange Online 使用 Exchange ActiveSync，則不是所有使用者都看到部門範本，就是所有使用者都看不到部門範本，這要視 Exchange Online 中的範本狀態 (保存或已發行) 而定。

    Office 2016 原本就支援部門範本，包含 Office 最新更新的 Office 2013 也是如此 ([KB 3054853](https://support.microsoft.com/kb/3054853))。

    > [!NOTE]
    > 如果您的應用程式原本就不支援部門範本，可以使用自訂的 RMS 範本下載指令碼或其他工具，將這些範本部署到本機的 RMS 用戶端資料夾。 然後，這些應用程式便會正確地只向您針對範本範圍所選取的使用者和群組顯示部門範本：
    > 
    > -   在 Office 2010 中，用戶端資料夾是 **%localappdata%\Microsoft\DRM\Templates**。
    > -   從已下載所有範本的用戶端電腦中，您可以複製範本檔案，然後將檔案貼到其他電腦。
    > 
    > 你可以[從 Microsoft Connect 網站下載自訂 RMS 範本指令碼](http://go.microsoft.com/fwlink/?LinkId=524506)。 若您按下此連結後看到錯誤，你可能尚未在 Microsoft Connect 註冊。   註冊：
    > 
    > 1.  請前往 [Microsoft Connect 網站](http://www.connect.microsoft.com)，並以您的 Microsoft 帳戶登入。
    > 2.  按一下 [目錄]，選擇 [檢視目前不接受回饋意見的 Connect 產品] 分類。
    > 3.  搜尋 **Rights Management Services**，在 [Microsoft RMS 企業功能] 方案上按一下 [加入]。

9. 按一下 [設定] 並新增使用者使用的其他語言，同時以該語言新增這個範本的名稱和描述。 當您有多語言使用者時，請務必新增他們使用的每一種語言，並以該語言提供名稱和描述。 那麼，使用者就會看見與他們的用戶端作業系統使用相同語言的範本名稱和描述，這樣可確保他們了解在文件或電子郵件訊息上套用的原則。 如果沒有與他們的用戶端作業系統相符的語言，他們所看見的名稱和描述就會切換回您最初建立範本時所定義的語言和描述。

    接著，請確認是否要對下列設定進行任何變更：

    |Setting|詳細資訊|
    |-----------|--------|
    |**內容到期**|為這個範本定義一個期限一到範本所保護的檔案便不應開啟的日期或天數。 您可以指定一個日期，或是指定從在檔案上套用保護的時間算起的天數。<br /><br />當您指定日期時，它會在您目前時區中的午夜生效。|
    |**離線存取**|使用這項設定可針對使用者必須能夠在沒有網際網路連線時開啟受保護檔案的需求，進行任何安全性需求的平衡。<br /><br />如果您指定沒有網際網路連線即無法使用內容，或是只有在指定的天數內可以使用內容，則當達到臨界值時，就必須重新驗證使用者和記錄其存取。 發生這種情況時，如果沒有快取他們的認證，系統就會提示使用者登入後才能開啟檔案。<br /><br />除了重新驗證之外，也會重新評估原則和使用者群組成員資格。 這表示如果自使用者上次存取檔案之後，原則或群組成員資格發生變更，使用者在同一個檔案就可能經歷不同的存取結果。|

10. 確信已經為您的使用者適當設定範本之後，請按一下 [發佈] 讓使用者可以看見範本，然後按一下 [儲存]。

11. 在傳統入口網站中，按一下 [上一頁] 按鈕返回 [範本] 頁面，頁面中會顯示範本現在的狀態已更新為 [已發佈]。

若要對範本進行任何變更，請選取它，然後再次使用快速入門步驟。 或是選取下列其中一個選項：

-   若要新增其他使用者和群組，並定義那些使用者和群組的權限：按一下 [權限]，然後按一下 [新增]。

-   若要移除您先前選取的使用者或群組：按一下 [權限]，從清單中選取使用者或群組，然後按一下 [刪除]。

-   若要變更可看到範本的使用者，請從應用程式選取：按一下 [範圍]，再按一下 [新增]、[刪除] 或 [應用程式相容性]。

-   若要讓範本不再被所有使用者看見：依序按一下 [設定]、[封存]，然後按一下 [儲存]。

-   若要進行其他組態變更：按一下 [設定]，進行變更，然後按一下 [儲存]。

> [!WARNING]
> 當您對先前儲存的範本進行變更時，用戶端必須等到他們電腦上的範本重新整理之後，才會看到您對範本所做的那些變更。 如需詳細資訊，請參閱本主題中的[重新整理使用者的範本](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_RefreshingTemplates)一節。

## <a name="BKMK_HowToCopyTemplates"></a>如何複製範本
如果您想要建立一個與現有範本的設定非常相似的新範本，請在 [範本] 頁面上選取原始範本、按一下 [複製]、指定一個唯一名稱，然後進行您所需的變更。

> [!IMPORTANT]
> 當您複製範本時，也會一併複製 [已發佈] 或 [已封存] 狀態。 因此，如果您複製一個已發佈的範本，其立即狀態也將是已發佈，除非您變更它。

您可以複製自訂範本和預設範本。 如果您想要範本將權限授與組織的所有使用者，則最佳作法是複製其中一個預設範本，而不是建立新的自訂範本。 此方法表示您不需要建立或選取多個群組來指定所有使用者。 不過，在此案例中，請一定要針對其他語言指定所複製範本的新名稱和說明。

## <a name="BKMK_HowToArchiveTemplates"></a>如何移除 (封存) 範本
無法刪除預設範本，但是可以封存它們，這樣使用者就看不到它們。

同樣地，如果您已經發佈一個自訂範本但是不想再要讓使用者看見它，則可以從 [設定] 頁面編輯該範本，然後選擇 [封存] 和 [儲存]。 或者您也可以從 [範本] 頁面選取它，然後選取 [封存]。

由於您無法編輯預設範本，因此若要封存這些範本，您就必須從 [範本] 頁面使用 [封存] 選項。 您無法封存 Outlook [不可轉寄] 選項。

#### 移除預設範本

-   從 [範本] 頁面，選取預設範本，然後按一下 [封存]。

狀態會從 [已發佈] 變更為 [已封存]。 如果您改變主意，請選取該範本，然後按一下 [發佈]。

## <a name="BKMK_RefreshingTemplates"></a>重新整理使用者的範本
當您使用 Azure RMS 時，範本會自動下載到用戶端電腦，讓使用者可以從他們的應用程式中選取這些範本。 不過，如果您對這些範本做了變更，可能就需要採取一些其他步驟：

|應用程式或服務|變更範本後如何重新整理範本|
|-----------|-----------------|
|Exchange Online|需要手動設定組態來重新整理範本。<br /><br />如需組態步驟，請展開下一節，[僅適用於 Exchange Online：如何設定 Exchange 下載已變更的自訂範本](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md#BKMK_ExchangeOnlineTemplatesUpdate)。|
|Office 365|自動重新整理 – 不需要其他步驟。|
|Office 2016 和 Office 2013<br /><br />適用於 Windows 的 RMS 共用應用程式|自動重新整理 – 透過排程：<br /><br />-   若為這些更新版本的 Office：預設重新整理間隔是每 7 天。<br />-   若為適用於 Windows 的 RMS 共用應用程式：從 1.0.1784.0 版開始，預設重新整理間隔是每 1 天。 舊版的預設值重新整理間隔是每 7 天。<br /><br />若要比這個排程更早強制執行重新整理，請展開下一節，[Office 2016、Office 2013 及 Windows 的 RMS 共用應用程式：如何強制重新整理已變更的自訂範本](#BKMK_Office2013ForceUpdate)。|
|Office 2010|在使用者登入時重新整理。<br /><br />若要強制重新整理，請要求或強制使用者登出後再重新登入。 或者，請參閱下一節：[僅適用於 Office 2010：如何強制重新整理已變更的自訂範本](#BKMK_Office2010ForceUpdate)。|
對於使用 RMS 共用應用程式的行動裝置，不需要設定其他組態，系統就會自動下載範本 (並在必要時重新整理)。

### <a name="BKMK_ExchangeOnlineTemplatesUpdate"></a>僅適用於 Exchange Online：如何設定 Exchange 下載已變更的自訂範本
如果您已經為 Exchange Online 設定資訊版權管理 (IRM)，在您於 Exchange Online 中使用 Windows PowerShell 進行下列變更之前，系統將不會為使用者下載自訂範本。

> [!NOTE]
> 如需關於如何在 Exchange Online 中使用 Windows PowerShell 的詳細資訊，請參閱[搭配 Exchange Online 使用 PowerShell](https://technet.microsoft.com/library/jj200677%28v=exchg.160%29.aspx)。

您必須在每次變更範本時都執行這個程序。

##### 更新 Exchange Online 的範本

1.  在 Exchange Online 中使用 Windows PowerShell，連線至服務：

    1.  提供您的 Office 365 使用者名和密碼：

        ```
        $Cred = Get-Credential
        ```

    2.  執行下列兩個命令連線到 Exchange Online 服務：

        ```
        $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell/ -Credential $Cred -Authentication Basic –AllowRedirection
        ```

        ```
        Import-PSSession $Session
        ```

2.  使用 [Import-RMSTrustedPublishingDomain](http://technet.microsoft.com/library/jj200724%28v=exchg.160%29.aspx) Cmdlet 從 Azure RMS 重新匯入信任的發佈網域 (TPD)：

    ```
    Import-RMSTrustedPublishingDomain -Name "<TPD name>" -RefreshTemplates -RMSOnline
    ```
    例如，如果您的 TPD 名稱是 **RMS Online - 1** (許多組織的典型名稱)，請輸入：**Import-RMSTrustedPublishingDomain -Name "RMS Online - 1" -RefreshTemplates -RMSOnline**

    > [!NOTE]
    > 若要驗證您的 TPD 名稱，您可以使用 [Get-RMSTrustedPublishingDomain](http://technet.microsoft.com/library/jj200707%28v=exchg.160%29.aspx) Cmdlet。

3.  若要確認是否已經成功匯入範本，請等候幾分鐘，然後執行 [Get-RMSTemplate](http://technet.microsoft.com/library/dd297960%28v=exchg.160%29.aspx) Cmdlet 並將類型設為全部。 例如：

    ```
    Get-RMSTemplate -TrustedPublishingDomain "RMS Online - 1" -Type All
    ```
    > [!TIP]
    > 保留輸出內容的副本十分有用，這麼做可讓您於稍後封存範本時輕鬆地複製範本名稱或 GUID。

4.  對於您希望可在 Outlook Web App 中使用的每個匯入的範本，您必須使用 [Set-RMSTemplate](http://technet.microsoft.com/library/hh529923%28v=exchg.160%29.aspx) Cmdlet，並將 Type 設為 Distributed：

    ```
    Set-RMSTemplate -Identity "<name  or GUID of the template>" -Type Distributed
    ```
    因為 Outlook Web Access 會快取 UI 24 小時，所以使用者可能會一整天都看不到新範本。

此外，如果您封存某個範本 (自訂或預設) 並使用 Exchange Online 搭配 Office 365，則當使用者使用 Outlook Web App 或採用了 Exchange ActiveSync 通訊協定的行動裝置時，將會繼續看見已封存的範本。

為了讓使用者不再看見這些範本，請在 Exchange Online 中使用 Windows PowerShell 來連線至服務，然後執行下列命令以使用 [Set-RMSTemplate](http://technet.microsoft.com/library/hh529923%28v=exchg.160%29.aspx) Cmdlet：

```
Set-RMSTemplate -Identity "<name or GUID of the template>" -Type Archived
```

### <a name="BKMK_Office2013ForceUpdate"></a>Office 2016、Office 2013 及 Windows 的 RMS 共用應用程式：如何強制重新整理已變更的自訂範本
藉由在執行 Office 2016、Office 2013 或 Windows 的 Rights Management (RMS) 共用應用程式的電腦上編輯登錄，您可以變更自動排程，使變更的範本在電腦上的重新整理頻率比它們的預設值更頻繁。 您也可以刪除登錄值中的現有資料來強制立即重新整理。

> [!WARNING]
> 如果您使用登錄編輯程式的方式不正確，可能會發生嚴重的問題而導致可能需要重新安裝作業系統。 Microsoft 無法保證您可以解決因不正確使用登錄編輯程式而導致的問題。 您需自行承擔使用登錄編輯程式的風險。

##### 變更自動排程

1.  使用登錄編輯程式，建立並設定下列其中一個登錄值：

    -   設定以天為單位的更新頻率 (最小值 1 天)：建立名為 **TemplateUpdateFrequency** 的新登錄值並為資料定義整數值，該值可指定下載任何已下載範本之變更的頻率，以天為單位。 使用下表來尋找登錄路徑以建立這個新的登錄值。

        |登錄路徑|類型|值|
        |--------|------|-----|
        |HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC|REG_DWORD|TemplateUpdateFrequency|

    -   設定以秒為單位的更新頻率 (最小值 1 秒)：建立名為 **TemplateUpdateFrequencyInSeconds** 的新登錄值並為資料定義整數值，該值可指定下載任何已下載範本之變更的頻率，以秒為單位。 使用下表來尋找登錄路徑以建立這個新的登錄值。

        |登錄路徑|類型|值|
        |--------|------|-----|
        |HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC|REG_DWORD|TemplateUpdateFrequencyInSeconds|

    請確定您建立並設定其中一個登錄值，不能兩者同時設定。 如果兩者均存在，**TemplateUpdateFrequency** 會被忽略。

2.  如果您想要強制立即重新整理範本，請移至下一個程序。 否則，立即重新啟動您的 Office 應用程式和 [檔案總管] 的執行個體。

##### 強制立即重新整理

1.  使用登錄編輯程式，刪除 **LastUpdatedTime** 值的資料。 例如，資料可能會顯示 **2015-04-20T15:52**，請刪除 2015-04-20T15:52，就不會顯示任何資料。 使用下表來尋找登錄路徑以刪除這個登錄值資料。

    |登錄路徑|類型|值|
    |--------|------|-----|
    |HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\&lt;MicrosoftRMS_FQDN&gt;\Template|REG_SZ|LastUpdatedTime|
    > [!TIP]
    > 在登錄路徑中，*&lt; MicrosoftRMS_FQDN &gt;* 指的是您的 Microsoft RMS 服務 FQDN。 如果您想要確認此值：
    > 
    > 1.  執行 Azure RMS 的 [Get-AadrmConfiguration](https://msdn.microsoft.com/library/windowsazure/dn629410.aspx) Cmdlet。 若尚未安裝適用於 Azure RMS 的 Windows PowerShell 模組，請參閱＜[針對 Azure Rights Management 安裝 Windows PowerShell](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md)＞。
    > 2.  從輸出中找出 **LicensingIntranetDistributionPointUrl** 值。
    > 
    >     例如：**LicensingIntranetDistributionPointUrl   : https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**
    > 3.  從該值，移除此字串的 **https://** and **/_wmcs/licensing**。 其餘的值為您的 Microsoft RMS 服務 FQDN。 在我們的範例中，Microsoft RMS 服務 FQDN 將為下列值：
    > 
    >     **5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

2.  刪除下列資料夾和其所包含的所有檔案：**%localappdata%\Microsoft\MSIPC\Templates**

3.  重新啟動您的 Office 應用程式和 [檔案總管] 的執行個體。

### <a name="BKMK_Office2010ForceUpdate"></a>僅適用於 Office 2010：如何強制重新整理已變更的自訂範本
藉由在執行 Office 2010 的電腦上編輯登錄，您可以設定一個值，讓變更的範本在電腦上重新整理，而不需要等待使用者登出與登入。 您也可以刪除登錄值中的現有資料來強制立即重新整理。

> [!WARNING]
> 如果您使用登錄編輯程式的方式不正確，可能會發生嚴重的問題而導致可能需要重新安裝作業系統。 Microsoft 無法保證您可以解決因不正確使用登錄編輯程式而導致的問題。 您需自行承擔使用登錄編輯程式的風險。

##### 變更更新頻率

1.  始用登錄編輯程式，建立名為 **UpdateFrequency** 的新登錄值並為資料定義整數值，該值可指定下載任何已下載範本之變更的頻率，以天為單位。 使用下表來尋找登錄路徑以建立這個新的登錄值。

    |登錄路徑|類型|值|
    |--------|------|-----|
    |HKEY_CURRENT_USER\Software\Microsoft\MSDRM\TemplateManagement|REG_DWORD|UpdateFrequency|

2.  如果您想要強制立即重新整理範本，請移至下一個程序。 否則，立即重新啟動您的 Office 應用程式。

##### 強制立即重新整理

1.  使用登錄編輯程式，刪除 **LastUpdatedTime** 值的資料。 例如，資料可能會顯示 **2015-04-20T15:52**，請刪除 2015-04-20T15:52，就不會顯示任何資料。 使用下表來尋找登錄路徑以刪除這個登錄值資料。

    |登錄路徑|類型|值|
    |--------|------|-----|
    |HKEY_CURRENT_USER\Software\Microsoft\MSDRM\TemplateManagement|REG_SZ|lastUpdatedTime|

2.  刪除下列資料夾和其所包含的所有檔案：**%localappdata%\Microsoft\MSIPC\Templates**

3.  重新啟動您的 Office 應用程式。

## <a name="BKMK_PowerShellTemplates"></a>Windows PowerShell 參考
您在 Azure 傳統入口網站中建立和管理範本所執行的一切動作，也可以從命令列利用 Windows PowerShell 來完成。 此外，您還可以匯出和匯入範本，以便在租用戶之間複製範本，或對範本中複雜的屬性進行整批編輯，例如多語系名稱和說明。

您可以也使用匯出和匯入來備份和還原您的自訂範本。最佳做法是定期備份您的自訂範本，而如果您進行意外的變更，即可輕易地復原為前一版。

> [!IMPORTANT]
> 若要使用 Windows PowerShell 建立和管理 Azure RMS 權限原則範本，您必須至少擁有 2.0.0.0 版的 [Windows PowerShell module for Azure RMS](http://go.microsoft.com/fwlink/?LinkId=257721)。
> 
> 如果您先前已安裝此 Windows PowerShell 模組，請在 PowerShell 視窗中執行下列命令來檢查版本號碼：`(Get-Module aadrm -ListAvailable).Version`

如需安裝指示，請參閱[針對 Azure Rights Management 安裝 Windows PowerShell](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md)。

支援建立和管理範本的 Cmdlet：

-   [Add-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727075.aspx)

-   [Export-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx)

-   [Get-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727079.aspx)

-   [Get-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727081.aspx)

-   [Import-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx)

-   [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx)

-   [Remove-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727082.aspx)

-   [Set-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx)

## 後續步驟
設定 Azure Rights Management 的自訂範本之後，請使用 [Azure Rights Management 部署藍圖](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) 來檢查將 [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] 轉出給使用者和系統管理員之前，是否還需要執行其他設定步驟。 若不需要執行其他設定步驟，請參閱[使用 Azure Rights Management](../Topic/Using_Azure_Rights_Management.md)取得操作指示，以支援組織的成功部署。

## 請參閱
[設定 Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

