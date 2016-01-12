---
description: na
keywords: na
title: Quick Start Tutorial for Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1db923bf-7d19-4fdd-a413-bfeb58af5e03
---
# Azure Rights Management 的快速入門教學指導
透過本教學課程所提供的 5 個步驟，您將能夠快速為組織試用 Microsoft Azure Rights Management (也稱為 Azure RMS)，所需時間不超過 15 分鐘。 您會啟動服務、透過電子郵件安全傳送機密文件給別的組織的人員，接著還能夠在文件被開啟時加以追蹤。 透過電子郵件送出的機密文件會在傳輸過程中加密，並且只有其收件者才能使用寄件者設定的權限加以讀取。

![](../Image/AzRMS_QuickStartStepsAll.PNG)

本教學課程的目標對象是 IT 系統管理員和顧問，目的是協助他們評估 Azure Rights Management 是否能夠做為組織的資訊保護解決方案。 在生產環境中，啟動服務的指示由系統管理員來執行，傳送文件的指示則由一般使用者執行。 本教學課程囊括這兩項指示，以示範將機密文件安全傳送給別的組織的人員的端對端案例。 如果您在完成本教學課程時遇到任何問題，請寄送電子郵件到 [AskIPTeam](mailto:askipteam@microsoft.com?subject=Having%20problems%20with%20the%20Quick%20Start%20tutorial)，我們會助您一臂之力。

若要完成本教學課程，您需要具備下列項目：

-   支援 Azure Rights Management 的訂閱。 付費或試用的訂閱都行。 如果您想要使用文件追蹤 (本教學課程的步驟 5 需要用到此功能)，您的訂閱必須支援文件追蹤。 如需訂閱選項和免費試用連結的詳細資訊，請參閱 [Azure Rights Management 的需求](../Topic/Requirements_for_Azure_Rights_Management.md)主題的[支援 Azure RMS 的雲端訂閱](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions)一節。

    提示：如果您需要取得訂閱，請事先進行，因為這項程序有時可能需要一段時間才能完成。

-   用來登入 Office 365 系統管理中心或是 Azure 傳統入口網站的系統管理員帳戶，以便能夠啟動 Rights Management 服務。 此帳戶也必須有電子郵件地址和工作電子郵件服務 (例如 Exchange Online 或 Exchange Server)。

-   執行 Windows (至少要是 Windows 7 SP1)，且已安裝 Office 2016、Office 2013 或 Office 2010 的電腦。

讓我們開始這次的教學。

## 步驟 1：啟動 Rights Management 服務
![](../Image/AzRMS_QuickStartSteps1.PNG)

雖然您擁有的訂閱可能會支援 Azure Rights Management，但這項服務預設是停用狀態。 若要啟動它，您可以使用 Office 365 系統管理中心或是 Azure 傳統入口網站：

-   如果您有包含 Azure Rights Management 的 Office 365 訂閱，或是所擁有的 Office 365 訂閱雖然沒有 Azure Rights Management，但您另外有 Azure RMS 進階版的訂閱：**使用 Office 365 系統管理中心**。

-   如果您沒有 Office 365 訂閱：**使用 Azure 傳統入口網站**。

![](../Image/AzRMS_Tutorial_1_Screenshots.png)

#### 若要從 Office 365 系統管理中心啟動 Rights Management

1.  移至 [Office 365 入口網站](https://portal.office.com/)，以您的工作或學校帳戶登入。

2.  如果 Office 365 系統管理中心未自動顯示，請選取左上角的應用程式啟動器圖示，並選擇 **[管理員]**。 只有 Office 365 管理員才會看到 **[管理員]** 方塊。

    > [!TIP]
    > 如需系統管理中心說明，請參閱 [關於 Office 365 系統管理中心 - 管理員說明](https://support.office.com/article/About-the-Office-365-admin-center-Admin-Help-58537702-d421-4d02-8141-e128e3703547)。

3.  展開左窗格中的 **[服務設定]**。

4.  按一下 **[Rights Management]**。

5.  在 **[RIGHTS MANAGEMENT]** 頁面上，按一下 **[管理]**。

6.  在 **[RIGHTS MANAGEMENT]** 頁面上，按一下 **[啟動]**。

7.  出現 **[是否要啟動 Rights Management?]**] 提示時，按一下 **[啟動]**。

現在，您應該會看到 **[Rights Management 已啟動]** 及用來停用的選項 (您可能需要手動重新整理頁面)。

此時請不要按 **[進階功能]**。 這會帶您到 Azure 傳統入口網站供您設定範本，但本教學課程不需要用到範本。 您反而可以關閉 Office 365 系統管理中心。

#### 從 Azure 入口網站啟動 Rights Management

1.  移至 [Azure 傳統入口網站](http://go.microsoft.com/fwlink/p/?LinkID=275081)並登入。

2.  在左窗格中，按一下 **[ACTIVE DIRECTORY]**。

3.  從 **[active directory]** 頁面中，按一下 **[RIGHTS MANAGEMENT]**。

4.  選取要為 [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] 管理的目錄，按一下 **[啟動]**，然後確認您的動作。

**[RIGHTS MANAGEMENT 狀態]** 現在應該會顯示為 **[作用中]**，且 **[啟動]** 選項會取代為 **[停用]**。

雖然您可以在入口網站設定 Rights Management 的其他選項，但本教學課程不需要用到這些選項，因此您可以關閉 Azure 傳統入口網站。

在第一個步驟中，您只需要做到這個程度就行。 將服務啟動，讓您組織中的所有使用者現在可以開始保護重要且敏感的文件。 在生產環境中，您可能會想要限制可以首先執行這項操作的使用者，以便分階段實作。 但在本教學課程中，則不需要這麼做。

雖然本文並未提及，但在生產部署期間，您可能也會想要設定自訂範本。 有了範本，使用者就能在需要保護檔案時，更輕鬆快速地套用正確設定。 您在啟動 Rights Management 時會自動獲得 2 個預設範本，並且您很可能會想讓生產環境中除了有這兩個預設範本外，再補上自己的自訂範本。 但本教學課程不需要用到範本，因此您已經可以進入下一個步驟。

|如果您想要更多的資訊|其他資訊|
|--------------|--------|
|關於啟動 Rights Management 以及控制誰可以在服務啟動時保護檔案和電子郵件   →|[啟用 Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md)|
|關於預設範本以及如何建立全新自訂範本   →|[設定 Azure Rights Management 的自訂範本](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md)|

## 步驟 2：安裝 Rights Management 共用應用程式
![](../Image/AzRMS_QuickStartSteps2.PNG)

Azure Rights Management 並不需要 Rights Management 共用應用程式 (也稱為「RMS 共用應用程式」)，但我們建議所有支援 Azure Rights Management 的電腦和行動裝置使用它。 RMS 共用應用程式會藉由安裝 Office 增益集來整合 Office 應用程式，讓使用者得以從功能區直接且輕易地保護檔案。 它還能夠藉由對 Azure Rights Management 並未原生支援的檔案套用一般保護，來保護所有檔案類型，並有文件追蹤網站可供使用者追蹤和撤銷他們所保護的檔案。 我們會在本教學課程後面用到文件追蹤網站。

此應用程式可免費下載，並有提供指令碼式安裝以供生產環境使用。 但在本教學課程中，我們會在本機進行安裝。

![](../Image/AzRMS_Tutorial_2_Screenshots.png)

#### 下載及安裝 Rights Management 共用應用程式

1.  移至 Microsoft 網站上的 [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) 頁面。

2.  在 **[電腦]** 區段中，按一下 **[適用於 Windows 的 RMS 應用程式]** 的圖示並儲存 **Setup.exe** 檔案，以安裝 Microsoft Rights Management 共用應用程式。

3.  若要進行本機安裝，您必須使用系統管理員帳戶來執行已下載的 Setup.exe 檔案。 如果系統提示您繼續進行，請按一下 **[是]**。

4.  在 [安裝 Microsoft RMS] 頁面上按 [下一步]，並等候安裝完成。

5.  當安裝完成時，如果系統提示您重新啟動電腦則按一下 **[重新啟動]**，否則請按一下 **[關閉]** 以完成安裝。

您現在已經可以開始保護內有想要只與所指定人員分享之資訊的檔案。

|如果您想要更多的資訊|其他資訊|
|--------------|--------|
|關於適用於 Windows 的 Rights Management 共用應用程式的本機安裝以及使用者指示   →|[Rights Management 共用應用程式使用者指南 (英文)](http://technet.microsoft.com/library/dn339006.aspx)|
|關於適用於 Windows 的 Rights Management 共用應用程式的指令碼式安裝以及更多技術資訊   →|[Rights Management 共用應用程式系統管理員指南 (英文)](http://technet.microsoft.com/library/dn339003.aspx)|
|了解原生保護和一般保護的差異   →|[一般保護和內建 (原生) 保護有何差異？](https://technet.microsoft.com/library/dn574738.aspx)|

## 步驟 3：以電子郵件傳送您想要保護的文件
![](../Image/AzRMS_QuickStartSteps3.PNG)

在此步驟中，請先使用 Word 建立並儲存一份文件來代表您想要保護的文件，並將它命名為 **Confidential.docx**。 在本教學課程中，這份文件實際包含什麼文字並不重要，但您勢必會想讓它包含一些文字，以便可以更輕鬆地確認獲得授權的收件者可以讀取此文件。 例如，您可以輸入：**如果您可以從電子郵件附件讀取這份文件，表示寄件者已成功共用以 Azure RMS 保護的檔案。**

接著，您就可以安全地透過電子郵件共用這份文件。

![](../Image/AzRMS_Tutorial_3_Screenshots.png)

#### 安全地透過電子郵件共用文件

1.  使用 Outlook 建立新的郵件，並附加您剛才建立的檔案。

2.  在 **[收件者]** 方塊中，輸入一或多個公司電子郵件地址。 請確定您指定的是公司電子郵件地址，例如 **janetm@contoso.com** 或 **p.dover@fabrikam.com**，因為 Azure Rights Management 目前並不支援您可能會在家裡使用的網際網路提供者所提供的個人電子郵件地址。 別擔心文件的收件者是否也有 Azure Rights Management。

3.  輸入主旨，例如**機密文件**，然後在電子郵件中輸入簡短訊息，例如**請閱讀這份機密文件，並請勿與他人共用。**

4.  然後，在 **[訊息]** 索引標籤的 **[RMS]** 群組中，按一下 **[共用保護]**，接著再按一下 **[共用保護]**：

5.  在 **[共用保護]** 對話方塊中：

    1.  選取 **[檢閱者 - 僅檢視]**。

        這表示我們的收件者將能夠檢視文件，但不能進行編輯或列印。

    2.  選取 **[有人嘗試開啟這些文件時傳送電子郵件給我]**。

        每當收件者嘗試開啟附件以及有其他人嘗試開啟時，例如收件者將電子郵件轉寄給同事，您就會收到電子郵件通知。 在最後一個案例中，您會看到存取遭到拒絕，而且您可以從使用者詳細資料來決定是否要傳送一份文件給該名人員，以便他能夠開啟。

    3.  選取 **[允許我立即撤銷這些文件的存取權]**。

        若選取這個選項，收件者每次開啟附件時都必須要有網際網路連線，但好處是如果您稍後撤銷文件，收件者下次嘗試開啟附件時，將不會成功。 如果您沒有選取這個選項，收件者即使沒有網際網路連線也可能可以開啟附件，但壞處是如果您稍後撤銷文件，其效果可能會延遲發生。

    4.  按一下 **[立即傳送]**。

        帶有附件的電子郵件就會傳送至您指定的電子郵件地址。 除了您寄送的電子郵件外，收件者還會看到相關指示，這些指示會說明如何讀取 Azure Rights Management 所保護的附加文件。

現在您已送出受保護的文件，因此您可以要求收件者等候其送達，然後將其開啟。 但請不要關閉 Outlook，因為我們會在最後一個步驟中再次用到它來追蹤附件。

|如果您想要更多的資訊|其他資訊|
|--------------|--------|
|保護透過電子郵件共用之檔案的完整指示和其他方法   →|[藉由使用 Rights Management 共用應用程式，保護您透過電子郵件共用的檔案](https://technet.microsoft.com/library/dn574735.aspx)|
|關於 **[共用保護]** 對話方塊中的選項   →|[Rights Management 共用應用程式的對話方塊選項](https://technet.microsoft.com/library/dn574738.aspx)|

## 步驟 4：要求收件者開啟以電子郵件送達的文件
![](../Image/AzRMS_QuickStartSteps4.PNG)

收件者可以使用多種裝置來讀取您以電子郵件附件傳送的受保護文件。 這些裝置包括 iPad、iPhone、Android 平板電腦和手機、Mac 電腦以及 Windows 電腦。

請要求他們閱讀您傳送的電子郵件。 他們會看到您的電子郵件，不過在此之前會先看到下列文字：

**寄件者已使用 Microsoft RMS 保護附件。您必須** [登入](http://aka.ms/rms)
      **才能開啟附件。**

當他們按下連結時，連結會將他們帶往用來安裝 RMS 共用應用程式以及在必要時註冊免費帳戶的指示。 免費帳戶會授與他們個人版 RMS 訂閱，以確保獲得授權的使用者一律可以讀取受保護的文件，即使其組織沒有 Azure RMS。 然後，他們就可以使用下列指示讀取受保護的附件。

![](../Image/AzRMS_Tutorial_4_Screenshots.png)

#### 檢視受保護的文件附件

1.  因為 Azure Rights Management 保護了 Word 文件，所以電子郵件內有兩個附件。 這兩個附件實際上是相同檔案的兩個版本，只是它們的副檔名不同。 開啟具有 **.ppdf** 副檔名的版本 (**Confidential.ppdf**)。

    如果[您裝置上的 Office 版本支援 Rights Management](https://technet.microsoft.com/library/dn655136.aspx)，您就可以開啟此檔案的另一個版本 (**Confidential.docx**)，讓它在 Word 中開啟。

2.  如果系統提示您輸入使用者名稱和密碼，請輸入與您用來傳送電子郵件和附件的電子郵件地址格式相同的使用者名稱。 例如 **janetm@contoso.com** 或 **p.dover@fabrikam.com**。 至於密碼，請輸入您註冊個人版 RMS 時所提供的密碼。 或者，如果貴組織擁有 Azure RMS，請輸入您平常的工作密碼。

文件隨即開啟，您現在可以讀取其內容。 例如，內容可能是說：「**如果您可以從電子郵件附件讀取這份文件，表示寄件者已成功共用以 Azure RMS 保護的檔案。**」因為是唯讀文件，您並無法變更其內容。

有一個選擇性步驟是，您可以要求收件者將電子郵件轉寄給不是原始電子郵件收件者的其他人。 即使這些人所服務的組織有 Azure Rights Management 或是他們本身申請自己的個人版 RMS 訂閱，他們還是無法開啟附件。 當系統提示他們輸入使用者名稱時，他們對於文件的存取便會遭到拒絕。

現在收件者已開啟附件並選擇性地將它轉寄給其他人，請期待您會收到報告此活動的電子郵件通知。 然而由於電子郵件很容易在經過一段時間後遺失，因此若要追蹤有誰存取過您的文件，比較好的方法是使用文件追蹤網站，最後一個步驟便是在講述這個方法。

|如果您想要更多的資訊|其他資訊|
|--------------|--------|
|用來檢視以 Azure Rights Management 保護之檔案的完整指示   →|[檢視並使用 Rights Management 保護的檔案](https://technet.microsoft.com/library/dn574741.aspx)|
|關於免費的個人版 RMS 訂閱   →|[個人版 RMS 和 Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md)|
|關於您看到的附加至電子郵件的兩個檔案版本   →|[什麼是自動建立的 .ppdf 檔案？](https://technet.microsoft.com/library/dn574738.aspx)|

## 步驟 5：追蹤受保護的文件
![](../Image/AzRMS_QuickStartSteps5.PNG)

> [!NOTE]
> 在此步驟中，您必須有支援文件追蹤的訂閱。 若要檢查您的訂閱是否包含文件追蹤，請參閱[比較 Rights Management Services (RMS) 所提供的功能](https://technet.microsoft.com/dn858608.aspx)。

這是選擇性步驟，但多數人都會想要知道他們傳送給別人的附件是否已開啟、其開啟時間，甚至是從哪裡開啟的。 例如：

-   您預期有人會在指定時間前回應您的郵件，但您在文件追蹤網站看到她還沒開啟過文件，截止時間已經快到了。 您傳送跟進電子郵件給她，或打電話及時提醒她。

-   看到有人開啟文件後，您接著向她詢問她是否有任何疑問或需要其他資訊。

![](../Image/AzRMS_Tutorial_5_Screenshots.png)

#### 追蹤受保護的文件

1.  使用 Outlook，在 **[首頁]** 索引標籤的 **[RMS]** 群組中，按一下 **[追蹤使用情況]**。

2.  如果您看到 **[由您保護和共用]** 頁面，按一下 **[登入]** 並再次提供您的使用者名稱和密碼。

3.  在 **[您共用的文件]** 頁面上，您會看到您附加至電子郵件的文件 **Confidential.docx**。 此時只有顯示這個檔案，若您共用其他受保護的文件，清單將會增加。

    在這個頁面中，您會看到文件的共用時間 (您何時傳送有受保護附加的電子郵件)、最後一次活動的日期，以及電子郵件寄送到的目標收件者的名稱。 按一下文件名稱以獲得其他詳細資料。

4.  在有您所點按之檔案名稱的新網頁上，您只會看到該文件的摘要詳細資料，以及該文件可用的其他選項清單 (**[清單]**、**[時間表]**、**[對應]**、**[設定]**)。

    按一下每個選項來瀏覽受保護文件的不同追蹤方式。 或是留在 **[摘要]** 頁面上，按一下 **[在 Excel 中開啟]** 將資訊匯出到試算表，或按一下 **[撤銷存取權]** 停止共用文件。

有必要時，您就可以回到這個網站來進一步追蹤受保護文件的活動，或撤銷其存取權。 您甚至可以從您的行動裝置或平板電腦的瀏覽器使用下列連結存取這個網站：[文件追蹤](http://go.microsoft.com/fwlink/?LinkId=529562)

|如果您想要更多的資訊|其他資訊|
|--------------|--------|
|用來追蹤文件的完整指示   →|[當您使用 RMS 共用應用程式時，追蹤及撤銷文件](https://technet.microsoft.com/library/dn986611.aspx)|
|說明和示範文件追蹤的兩分鐘影片   →|[Azure RMS 文件追蹤和撤銷](http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation)|
|疑難排解和客戶問題   →|[文件追蹤的常見問題集](https://technet.microsoft.com/dn947488)|

## 後續步驟
本教學課程只有帶領您逐步了解 Azure RMS 如何協助保護資料的其中一個案例。 若要查看其他常見的使用案例，請參閱[什麼是 Azure Rights Management？](../Topic/What_is_Azure_Rights_Management_.md) 文章中的 [Azure RMS 運作方式](https://technet.microsoft.com/library/jj585026.aspx)一節。 此文章中還有可能對您也有幫助的其他章節，例如 Azure RMS 是如何運作的以及它能解決哪些商務問題。

如果您已準備好開始部署 Azure RMS，請使用 [Azure Rights Management 部署藍圖](../Topic/Azure_Rights_Management_Deployment_Roadmap.md) 作為您的部署步驟和作法指示的連結。

## 請參閱
[開始使用 Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

