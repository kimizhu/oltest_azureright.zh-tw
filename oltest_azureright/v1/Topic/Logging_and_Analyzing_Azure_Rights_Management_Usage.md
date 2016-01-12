---
description: na
keywords: na
title: Logging and Analyzing Azure Rights Management Usage
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a735f3f7-6eb2-4901-9084-8c3cd3a9087e
---
# 記錄和分析 Azure Rights Management 使用情況
請參閱本主題的資訊來協助您了解如何使用 Azure Rights Management (Azure RMS) 的使用情況記錄功能。 Azure Rights Management 服務RMS 可以記錄它對您的組織所做的每一個要求，包括來自使用者的要求、由組織中的 RMS 系統管理員所執行的動作，以及 Microsoft 操作員為了支援 Azure Rights Management 部署而執行的動作。

然後，您可以利用這些 Azure Rights Management 記錄來支援下列商務案例：

-   分析商業見解。

    Azure Rights Management 採用 W3C 擴充記錄格式將記錄寫入您提供的 Azure 儲存體帳戶。 所以，您可以將這些記錄寫入您選擇的存放庫 (例如資料庫、線上分析處理 (OLAP) 系統或 map-reduce 系統)，以分析資訊並產生報告。 例如，您可以識別誰存取 RMS 保護的資料。 您可以判斷使用者存取 RMS 保護的哪些資料，以及從什麼裝置和從哪裡存取。 您可以查明使用者是否可順利讀取受保護的內容。 您也可以識別哪些使用者已讀取受保護的重要文件。

-   監督濫用情形。

    Azure Rights Management 記錄為您提供的幾乎都是即時資訊，所以您可以持續監視公司如何使用 Azure Rights Management。 99.9% 的記錄會在 RMS 起始動作之後的 15 分鐘內產生。

    例如，當正常工作時段外突然有許多使用者讀取 RMS 保護的資料，您可能希望獲得警示，這可能表示有惡意使用者正在收集資訊來販售給競爭對手。 或者，同一個使用者很明顯在極短的時間內從兩個不同的 IP 位址存取資料，這可能表示使用者帳戶已被盜用。

-   執行蒐證分析。

    如果發生資訊外洩，您可能會被問及誰最近存取特定的文件，以及可疑人士最近存取什麼資訊。 只要有使用 Azure Rights Management 和記錄，您就能夠回答這幾種問題，因為使用受保護內容的人一定要取得 Azure Rights Management 授權才能開啟 Azure Rights Management 所保護的文件和圖片，即使這些檔案由電子郵件移動，或複製到 USB 磁碟機或其他存放裝置也一樣。 這表示當您使用 Azure Rights Management 來保護資料時，Azure Rights Management 記錄可當做可靠的資訊來源以進行蒐證分析。

> [!NOTE]
> 如果您只對記錄 Azure Rights Management 的管理工作有興趣，並且不想要追蹤使用者使用 Rights Management 的方式，您可以針對 Azure Rights Management 使用 Windows PowerShell Cmdlet [Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx)。
> 
> 您也可以使用 Azure 傳統入口網站，取得高階使用情況報告，其中包含 **RMS 使用情況**、**最活躍的 RMS 使用者**、**RMS 裝置使用情況**，以及**啟用 RMS 的應用程式使用情況**。 若要從 Azure 傳統入口網站存取這些報告，請按一下 [Active Directory]、選取並開啟目錄，然後按一下 [報告]。

如需 Azure Rights Management 使用情況記錄的詳細資訊，請參閱下列幾節。

-   [如何啟用 Azure Rights Management 使用情況記錄](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_EnableRMSLogging)

-   [如何存取和使用 Azure Rights Management 使用情況記錄](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_AccesAndUseLogs)

-   [如何管理 Azure Rights Management 記錄儲存體](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_ManageStorage)

-   [如何委派 Azure Rights Management 使用情況記錄的存取權](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Delegate)

-   [如何解讀 Azure Rights Management 使用情況記錄](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Interpret)

-   [Windows PowerShell 參考](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_PowerShell)

## <a name="BKMK_EnableRMSLogging"></a>如何啟用 Azure Rights Management 使用情況記錄
Azure Rights Management 使用情況記錄為選用，如果想要使用，您必須採用特定的步驟。 使用 Azure Rights Management 使用情況記錄時，Rights Management 運作方式不會改變，而記錄程序本身為免費。 不過，您必須為記錄提供 Azure 儲存體帳戶，將會針對此儲存體而向您收費。

開始之前，請確定您符合以下使用 Azure Rights Management 使用情況記錄的先決條件：

|需求|詳細資訊|
|------|--------|
|IT 管理的訂用帳戶，其中包含 Azure Rights Management|您必須有組織所管理的 Azure Rights Management 訂閱。 使用個人版 RMS 的組織無法使用 Azure Rights Management 使用情況記錄。<br /><br />如果組織具有使用個人版 RMS 的使用者，則 Azure Rights Management 使用情況記錄有極具說服力的理由將個別版 RMS 轉換成 Microsoft Azure Rights Management 訂閱。<br /><br />如需包含 Azure RMS 之訂用帳戶的詳細資訊，請參閱＜[支援 Azure RMS 的雲端訂閱](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions)＞主題的＜[Azure Rights Management 的需求](../Topic/Requirements_for_Azure_Rights_Management.md)＞一節。<br /><br />如需個人版 RMS 的詳細資訊，請參閱＜[個人版 RMS 和 Azure Rights Management](../Topic/RMS_for_Individuals_and_Azure_Rights_Management.md)＞|
|Azure 訂閱|您必須訂閱 Azure，且在 Azure 上有足夠的儲存體可供 Azure Rights Management 記錄使用。|
|Windows PowerShell for Azure Rights Management|如果尚未這樣做，請下載並安裝適用於 Azure Rights Management 的 Windows PowerShell。 您將使用 Windows PowerShell Cmdlet 來設定和管理 Azure Rights Management 使用情況記錄。<br /><br />如需詳細資訊，請參閱[針對 Azure Rights Management 安裝 Windows PowerShell](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md)。|
請使用下列程序來啟用 Azure Rights Management 使用情況記錄，其中包括步驟來建立 Azure 儲存體帳戶，然後設定 Azure 使用此儲存體帳戶來儲存 Azure Rights Management 記錄。

> [!NOTE]
> 此程序假設您有 Azure 帳戶。 Azure Rights Management 使用情況記錄支援個別帳戶，但建議使用工作或學校帳戶。 此外，建議您為 Rights Management 記錄建立專用的儲存體帳戶。 您必須將儲存體存取金鑰分享給 Azure Rights Management，以及可能也會使用記錄檔的其他人。
> 
> 如需 Azure 儲存體的詳細資訊，請參閱＜[針對儲存體的 Azure 文件](http://azure.microsoft.com/documentation/services/storage/)＞。

#### 如何建立儲存體帳戶和啟用 Azure Rights Management 記錄

1.  登入 [Azure 入口網站](https://portal.azure.com/)。

2.  在 [集線器] 功能表中，選擇 [新增] -&gt; [資料 + 儲存體] -&gt; [儲存體帳戶]。

    > [!TIP]
    > 如果看不到這個選項，請檢查除了您針對 Rights Management 的訂用帳戶外，是否還有 Azure 訂用帳戶。

3.  保留預設的 [傳統] 部署模型，然後按一下 [建立]。

    指定儲存體帳戶的名稱，如有必要，變更 [定價層]、[資源群組]、[訂閱] 以及是否要 [釘選到儀表板] 的選定選項。 然後，按一下 [建立]。 等待 [建立儲存體帳戶] 活動完成。

4.  按一下新建立的儲存體帳戶，然後按一下 [設定]。

5.  在 [設定] 刀鋒視窗中，按一下金鑰圖示。

6.  在 [管理金鑰] 刀鋒視窗中，複製 [主要存取金鑰]  的值，關閉刀鋒視窗。

7.  使用 [**以系統管理員身分執行**] 選項啟動 Windows PowerShell。 執行 [Connect-AadrmService](https://msdn.microsoft.com/library/azure/dn629415.aspx) 命令，以連接至 Azure Rights Management 服務：

    ```
    Connect-AadrmService
    ```

8.  使用 [Set-AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629426.aspx) 命令來指定您要將 Azure Rights Management 使用情況記錄保存在何處，並將 *&lt;Access_Key&gt;* 換成您在步驟 6 中複製的主要存取金鑰，將 *&lt;StorageAccount&gt;* 換成您在步驟 3 中建立的儲存體帳戶名稱。

    ```
    $accesskey = convertto-securestring -asplaintext -force –string <Access_Key> Set-AadrmUsageLogStorageAccount -AccessKey $accesskey -StorageAccount <StorageAccount>
    ```

9. 使用[Enable-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629421.aspx) 命令來啟用 Azure Rights Management 使用情況記錄：

    ```
    Enable-AadrmUsageLogFeature
    ```
    您應該會看到此訊息：**權限管理服務已啟用使用記錄功能。**

現在已啟用使用情況記錄，Azure Rights Management 會開始記錄您組織的所有動作，並將此資訊儲存到您的儲存體帳戶。 在此之前不會產生記錄資訊。

如需如何建立儲存體帳戶的詳細資訊，請參閱 Azure 文件中＜[關於 Azure 儲存體](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/)＞的＜[建立儲存體帳戶](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/)＞一節。

## <a name="BKMK_AccesAndUseLogs"></a>如何存取和使用 Azure Rights Management 使用情況記錄
Azure Rights Management 會以一連串 Blob 將記錄寫入 Azure 儲存體帳戶。 每一個 Blob 包含一或多筆記錄 (W3C 擴充記錄格式)。 Blob 名稱是依建立順序排列的數字。 本文稍後的＜[如何解讀 Azure Rights Management 使用情況記錄](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Interpret)＞一節包含記錄內容及其建立方式的詳細資訊。

發生 Azure Rights Management 動作之後需要一些時間，記錄才會出現在儲存體帳戶中。 大多數記錄會在 15 分鐘內出現。

您為 Azure Rights Management 使用情況記錄所建立的儲存體帳戶就像信箱一樣，支援直接讀取儲存體帳戶，但這並不是最佳使用方式。 反之，為了獲得最佳效能和降低成本，建議您將記錄下載到本機儲存體，例如本機資料夾、資料庫或 map-reduce 儲存機制。

有兩種方式可下載使用情況記錄：

-   使用 Windows PowerShell Cmdlet [Get-AadrmUsageLog](https://msdn.microsoft.com/library/azure/dn629401.aspx)。

    這是存取使用情況記錄最簡單的方式。 此 Cmdlet 可將記錄下載到您的電腦，將每一個 Blob 當成檔案下載到您指定的位置。

-   使用 [Azure 儲存體 SDK](http://www.windowsazure.com/en-us/develop/net/) 撰寫您自己的自訂應用程式來下載記錄。

    自訂應用程式的彈性比 Get-AadrmUsageLogs Cmdlet 更大。 例如，您可以將下載記錄的工作委派給不得使用 Azure Rights Management 管理認證的某人或程序。 或者，因為想要監督濫用情形，您可以即時輪詢記錄。

#### 使用 PowerShell 下載使用情況記錄

-   使用 [以系統管理員身分執行] 選項啟動 Windows PowerShell 並執行 **Get-AadrmUsageLog –Path &lt;location&gt;**。 例如，在您的 E 磁碟機上建立一個名為 **logs** 的資料夾：

    -   若要將所有可用的記錄下載到 E:\logs 資料夾：`Get-AadrmUsageLog -Path "e:\logs"`

    -   若要下載特定範圍的 Blob：`Get-AadrmUsageLog –Path "e:\logs" –FromCounter 1024 –ToCounter 2047`

執行這些 Cmdlet 時，Windows PowerShell 會顯示最後一個下載的 Blob 的名稱。 您可以此名稱指定給變數，讓您在迴圈或排程工作中執行 Get-AadrmUsageLog，每次只下載累加的記錄。

例如：

**PS C:\&gt; $LastBlobName = Get-AadrmUsageLog –Path "e:\logs"**

**1527**

**PS C:\&gt; $LastBlobName**

**1527**

> [!TIP]
> 您可以使用 [Microsoft 的記錄檔剖析器](http://www.microsoft.com/download/details.aspx?id=24659) (這是用來在各種已知的記錄檔格式之間轉換的工具)，將您的所有已下載記錄檔彙總為 CSV 格式。 您也可以利用此工具將資料轉換成 SYSLOG 格式，或匯入到資料庫中。 安裝此工具之後，請執行 **LogParser.exe /?**，以取得使用此工具的說明和資訊。 例如，您可以執行下列命令將所有資訊匯入到 .log 檔案格式：**logparser –i:w3c –o:csv “SELECT &#42; INTO AllLogs.csv FROM &#42;.log”**。

您可以暫停和繼續使用情況記錄。 暫停記錄時，Azure Rights Management 會保留您的儲存體帳戶資訊，讓您可以輕鬆地繼續記錄。

#### 暫停和繼續使用情況記錄

-   若要暫停記錄，請使用下列 Cmdlet：[Disable-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629404.aspx)

-   若要繼續記錄，請使用下列 Cmdlet：[Enable-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629421.aspx)

-   若要檢查記錄是否啟用或停用，請使用下列 Cmdlet：[Get-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629425.aspx)

    值為 **True** 表示已啟用 Azure Rights Management 的使用情況記錄，值為 **False** 表示已停用記錄。

## <a name="BKMK_ManageStorage"></a>如何管理 Azure Rights Management 記錄儲存體
我們會針對用來保存 Azure Rights Management 記錄的儲存體空間而向您收費。

Azure Rights Management 不會自動管理您的使用情況記錄檔。 如果您未採取任何動作，則它們會留在您的儲存體帳戶內。 不過，為了節省空間和降低儲存體成本，您可以在下載之將它們刪除。 或者，您也可以選擇想要刪除的檔案。 有一個例外是 Azure Rights Management 不會使用這些記錄檔，所以您隨時都可以刪除它們。

不可刪除 (或修改) 的檔案在 **rms-metadata** 容器中名為**中繼資料**。 Azure Rights Management 會使用此 Blob 來追蹤最後一個使用的 Blob 號碼。 如果刪除此檔案，Azure Rights Management 會為記錄建立新的容器，Blob 號碼從 1 起算，而此後使用 Get-AadrmUsageLog Cmdlet 的所有下載工作都會使用這個新的容器來下載記錄檔。 因此，原始容器中的任何記錄會保留，但變成孤立。 只有利用 Azure 儲存體 SDK 才能下載這些孤立的記錄。

> [!TIP]
> 您可以透過分享您的儲存體帳戶名稱和存取金鑰，將此管理功能委派給其他公司，而不必自行管理 Azure Rights Management 記錄儲存體。 如需相關資訊，請參閱本主題後續的章節＜[如何委派 Azure Rights Management 使用情況記錄的存取權](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_Delegate)＞。

在某些情況下，您可能想要重新產生儲存體存取金鑰。 例如：

-   您更換負責管理 Azure Rights Management 使用情況記錄的公司。

-   您懷疑儲存體存取金鑰被盜。

如果發生此狀況，您就必須使用次要存取金鑰 (假設您先前使用主要存取金鑰)，以確保服務不中斷。 當您重新產生先前未使用的存取金鑰時，您必須設定 Azure Rights Management 來使用新的金鑰。 請使用下列程序來重新產生次要存取金鑰並設定 Azure Rights Management 來使用它：

#### 重新產生次要存取金鑰

1.  登入 [Azure 入口網站](https://portal.azure.com/)。

2.  按一下 [所有資源]，在文字方塊中輸入您的儲存體名稱以搜尋儲存體。

3.  選取您的儲存體，按一下 [設定]。

4.  按一下金鑰圖示。

5.  在 [管理金鑰] 區段中，按一下 [重新產生次要金鑰]，再按一下 [是]確認要重新產生次要存取金鑰，並將新的次要存取金鑰複製到剪貼簿。

    請勿關閉 Azure 入口網站。

6.  使用 [以系統管理員身分執行] 選項啟動 Windows PowerShell，並使用 [Set-AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629426.aspx) Cmdlet 將 Azure Rights Management 設定為使用這個新的存取金鑰，將 *&lt;StorageAccount&gt;* 換成您的儲存體帳戶名稱，將 *&lt;Access_Key&gt;* 換成您剛複製的重新產生的次要存取金鑰：

    ```
    Set-AadrmUsageLogStorageAccount -StorageAccount <StorageAccount>-AccessKey <Access_Key>
    ```
    > [!WARNING]
    > 雖然您在執行此命令時可以切換至另一個儲存體帳戶，但此動作會使先前的記錄變成孤立，而無法再由 Set-AadrmUsageLogStorageAccount 或類似的管理命令和函數來存取。

7.  回到 Azure 入口網站的 [管理金鑰] 區段，重新產生主要存取金鑰。

如需如何管理儲存體存取金鑰的詳細資訊，請參閱 Azure 文件中＜[關於 Azure 儲存體帳戶](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/)＞的＜[管理儲存體存取金鑰](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/)＞一節。

## <a name="BKMK_Delegate"></a>如何委派 Azure Rights Management 使用情況記錄的存取權
您可以經由分享儲存體帳戶名稱和存取金鑰來委派 RMS 記錄的存取。 您可以將存取權委派給另一個管理使用者、您組織內的開發人員，或獨立軟體廠商 (ISV)。 因為他們沒有您的 RMS 系統管理員認證，所以無法使用 Get-AardrmUsageLog Cmdlet 來下載 RMS 記錄。 反之，他們必須使用 Windows 儲存體 SDK 才能下載記錄。 或者，他們也可以撰寫應用程式來直接從 Azure 儲存體讀取記錄。

只要儲存體帳戶是 RMS 記錄專用，這樣分享您的儲存體帳戶名稱和存取金鑰很安全。 即使其他人有您的存取金鑰，也無法用來存取其他任何儲存體帳戶或使用您的 RMS 租用戶帳戶。

## <a name="BKMK_Interpret"></a>如何解讀 Azure Rights Management 使用情況記錄
使用下列資訊來協助您解讀 Azure Rights Management 使用情況記錄。

### 儲存體帳戶配置
Azure Rights Management 第一次將記錄寫入儲存體帳戶時會建立下列兩個容器：

-   **Rms-metadata**：此容器保留供 Azure Rights Management 使用。 請不要修改或刪除此容器。

-   **Rms-logs-&lt;guid&gt;**：此容器是 Azure Rights Management 建立和儲存記錄的地方。 如果不想再記錄此容器中的任何檔案所包含的資訊，您可以安心地刪除此容器中的任何檔案。

經過一段時間，Azure Rights Management 可能會建立其他 **Rms-logs-&lt;guid&gt;** 容器。 例如，如果 **Rms-metadata** 容器損毀或意外刪除，Azure Rights Management 會重設其內容並建立新的 **Rms-logs-&lt;guid&gt;** 容器來儲存所有未來的記錄。 舊容容中的舊記錄不會刪除，但會變成孤立。

### 記錄順序
Azure Rights Management 會以一連串 Blob 來寫入記錄。 每一個 Blob 包含一或多筆記錄 (W3C 擴充記錄格式)。

每一個 Blob 的名稱都是數字。 在每一個記錄容器內，將第一個 Blob 命名為 000000001。 每個 Blob 會依其建立順序來循序命名。 每一個 Blob 包含一或多筆記錄。 每一筆記錄都有 UTC 時間戳記指出 Azure Rights Management 何時處理對應的要求。

> [!IMPORTANT]
> Azure Rights Management 記錄系統經過最佳化可快速提供記錄，而非依嚴格的循序順序提供。 Blob 的順序汲 Blob 內的記錄順序可能不會按照時間順序。 Blob 循序命名的唯一理由是為了讓您有效率地遞增下載。
> 
> 記錄順序結果的兩個範例：
> 
> -   Blob 000000004 中的記錄檔記錄可能會依時間先後順序與 Blob 000000003 中的記錄檔記錄重疊。 在罕見的情況下，可能已在 Blob 000000003 中的所有記錄檔記錄之前產生 Blob 000000004 中的所有記錄檔記錄。
> -   Blob 中的第二筆記錄可能在第一筆記錄之前產生，但以相反的順序寫入儲存體。

在分析 Azure Rights Management 記錄之前，建議下載記錄並匯入至存放庫，讓您可在其中依時間戳記來排序記錄。 如需下載記錄的詳細資訊，請參閱本主題中的＜[如何存取和使用 Azure Rights Management 使用情況記錄](../Topic/Logging_and_Analyzing_Azure_Rights_Management_Usage.md#BKMK_AccesAndUseLogs)＞一節。

因為記錄不一定按照時間順序，但大多數會在要求的 15 分鐘內寫入，當您依時間戳記來識別想要的記錄時，請將您要的時間再加上 15 分鐘。 然後下載這些記錄。 此策略應該可確保您幾乎取得所有記錄。

另外一件要記住的事，每一筆記錄的時間戳記就是處理要求的 Azure Rights Management 服務的本地時間。 因為 Azure Rights Management 是跨多個資料中心而在多個伺服器上執行，即使記錄依時間戳記排序，有時也可能不按照順序。 不過，差異很小，通常只在一分鐘內。 在大部分情況下，這不會對記錄分析造成問題。

### Blob 格式
每一個 Blob 都是 W3C 擴充記錄格式。 開頭為下列兩行：

**#Software:RMS**

**#Version:1.1**

第一行識別這些是 Azure Rights Management 的記錄。 第二行識別 Blob 的其餘部分都遵循 1.1 版規格。 建議任何可剖析這些記錄的應用程式在繼續剖析 Blob 的其餘部分之前，先驗證這兩行。

第三行列舉以 Tab 鍵分隔的欄位名稱清單：

**#Fields: date            time            row-id        request-type           user-id       result          correlation-id          content-id                owner-email           issuer                     template-id             file-name                  date-published      c-info         c-ip**

後續每一行都是記錄。 欄位的值與前一行的順序相同，以 Tab 鍵隔開。 請使用下表來解讀欄位。

|欄位名稱|W3C 資料類型|說明|範例值|
|--------|------------|------|-------|
|date|日期|處理要求時的 UTC 日期。<br /><br />來源是處理要求的伺服器的本機時鐘。|2013-06-25|
|time|時間|處理要求的 UTC 時間 (24 小時制)。<br /><br />來源是處理要求的伺服器的本機時鐘。|21:59:28|
|row-id|文字|此記錄的唯一 GUID。<br /><br />將記錄彙總或將記錄複製成另一種格式時，此值很有用。|1c3fe7a9-d9e0-4654-97b7-14fafa72ea63|
|request-type|名稱|要求的 RMS API 的名稱。|AcquireLicense|
|user-id|字串|提出要求的使用者。<br /><br />值以單引號括住。 部分要求類型為匿名，此時值為 ”。|‘joe@contoso.com’|
|result|字串|‘Success’ 表示成功處理要求。<br /><br />要求失敗時以單引號括住的錯誤類型。|‘Success’|
|correlation-id|文字|某個特定要求在 RMS 用戶端記錄和伺服器記錄之間的共同 GUID。<br /><br />對用戶端問題進行疑難排解時，此值很有用。|cab52088-8925-4371-be34-4b71a3112356|
|content-id|文字|識別受保護內容 (例如文件) 的 GUID (以大括孤括住)。<br /><br />只有當 request-type 是 AcquireLicense 時，此欄位才有值，至於其他所有要求類型，此欄位會空白。|{bb4af47b-cfed-4719-831d-71b98191a4f2}|
|owner-email|字串|文件擁有者的電子郵件地址。|alice@contoso.com|
|issuer|字串|文件簽發者的電子郵件地址。|alice@contoso.com (或) FederatedEmail.4c1f4d-93bf-00a95fa1e042@contoso.onmicrosoft.com'|
|Template-id|字串|用來保護文件的範本 ID。|{6d9371a6-4e2d-4e97-9a38-202233fed26e}|
|File-name|字串|受保護的文件的檔案名稱。|TopSecretDocument.docx|
|Date-published|日期|文件受保護的日期。|2015-10-15T21:37:00|
|c-info|字串|提出要求的用戶端平台的相關資訊。<br /><br />具體字串隨著應用程式而不同 (例如，作業系統或瀏覽器)。|'MSIPC;version=1.0.623.47;AppName=WINWORD.EXE;AppVersion=15.0.4753.1000;AppArch=x86;OSName=Windows;OSVersion=6.1.7601;OSArch=amd64'|
|c-ip|位址|提出要求的用戶端的 IP 位址。|64.51.202.144|

#### user-id 欄位的例外狀況
雖然 user-id 欄位通常指出提出要求的使用者，但有兩種例外狀況，值不會對應至真正的使用者：

-   值 **'microsoftrmsonline@&lt;YourTenantID&gt;.rms.&lt;region&gt;.aadrm.com'**。

    這指出 Office 365 服務 (例如 Exchange Online 或 Sharepoint Online) 正提出要求。 在字串中，*&lt;YourTenantID&gt;* 是租用戶的 GUID，*region&gt;* 是租用戶註冊的地區。 例如，**na** 代表北美洲、**eu** 代表歐洲，**ap** 代表亞洲。

-   如果您使用 RMS 連接器，

    則會以服務主體名稱來記錄來自此連接器的要求，當您安裝 RMS 連接器時，RSM 會自動產生服務主體名稱。

#### 一般要求類型
Azure Rights Management 有許多要求類型，下表指出一些最常用的要求類型。

|要求類型|說明|
|--------|------|
|AcquireLicense|來自 Windows 電腦的用戶端要求對 RMS 保護內容的授權。|
|AcquirePreLicense|用戶端代表使用者要求對 RMS 保護內容的授權。|
|AcquireTemplates|進行呼叫，以取得根據範本 ID 的範本。|
|AcquireTemplateInformation|進行呼叫，以從服務取得範本的 ID。|
|AddTemplate|從 Azure 傳統入口網站進行呼叫，以新增範本。|
|BECreateEndUserLicenseV1|從行動裝置進行呼叫，以建立使用者授權。|
|BEGetAllTemplatesV1|從行動裝置 (後端) 進行呼叫，以取得所有範本。|
|Certify|用戶端認證保護的內容。|
|Decrypt|用戶端嘗試解密 RMS 保護的內容。|
|DeleteTemplateById|從 Azure 傳統入口網站進行呼叫，以刪除範本 ID 的範本。|
|ExportTemplateById|從 Azure 傳統入口網站進行呼叫，以匯出範本 ID 的範本。|
|FECreateEndUserLicenseV1|類似於 AcquireLicense 要求，來自於行動裝置。|
|FECreatePublishingLicenseV1|與 Certify 結合 GetClientLicensorCert 相同，來自行動用戶端。|
|FEGetAllTemplates|從行動裝置 (前端) 進行呼叫，以取得範本。|
|GetAllTemplates|從 Azure 傳統入口網站進行呼叫，以取得所有範本。|
|GetClientLicensorCert|用戶端從 Windows 電腦要求發佈憑證 (稍後用來保護內容)|
|GetConfiguration|呼叫 Azure PowerShell Cmdlet，以取得 Azure RMS 租用戶的組態。|
|GetConnectorAuthorizations|從 RMS 連接器進行呼叫，以從雲端取得其組態。|
|GetTenantFunctionalState|Azure 傳統入口網站檢查 Azure RMS 是否啟動。|
|GetTemplateById|從 Azure 傳統入口網站進行呼叫，以取得指定範本 ID 的範本。|
|ExportTemplateById|從 Azure 傳統入口網站進行呼叫，以匯出指定範本 ID 的範本。|
|FindServiceLocationsForUser|進行呼叫以查詢 URL，用呼叫 Certify 或 AcquireLicense。|
|ImportTemplate|從 Azure 傳統入口網站進行呼叫，以匯入範本。|
|ServerCertify|從已啟用 RMS 的用戶端 (如 SharePoint) 進行呼叫，以認證伺器。|
|SetUsageLogFeatureState|進行呼叫，以啟用使用情況記錄。|
|SetUsageLogStorageAccount|進行呼叫，以指定 Azure RMS 記錄的位置。|
|SignDigest|當因為簽章目的而使用金鑰時，進行呼叫。 通常每個 AcquireLicence (或 FECreateEndUserLicenseV1)、Certify 及 GetClientLicensorCert (或 FECreatePublishingLicenseV1) 只會呼叫一次。|
|UpdateTemplate|從 Azure 傳統入口網站進行呼叫，以更新現有範本。|

## <a name="BKMK_PowerShell"></a>Windows PowerShell 參考
請使用下列 Windows PowerShell Cmdlet 來協助您設定和使用 RMS 使用情況記錄：

-   [Disable-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629404.aspx)

-   [Enable-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629421.aspx)

-   [Get-AadrmUsageLog](https://msdn.microsoft.com/library/azure/dn629401.aspx)

-   [Get-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629425.aspx)

-   [Get-AadrmUsageLogLastCounterValue](https://msdn.microsoft.com/library/azure/dn629423.aspx)

-   [Get-AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629419.aspx)

-   [Set-AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629426.aspx)

如需在 Azure Rights Management 使用 Windows PowerShell 的詳細資訊，請參閱＜[使用 Windows PowerShell 管理 Azure Rights Management](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md)＞。

## 請參閱
[使用 Azure Rights Management](../Topic/Using_Azure_Rights_Management.md)

