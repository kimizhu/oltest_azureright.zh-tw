---
description: na
keywords: na
title: Operations for Your Azure Rights Management Tenant Key
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1284d0ee-0a72-45ba-a64c-3dcb25846c3d
---
# Azure Rights Management 租用戶金鑰的作業
根據租用戶金鑰拓撲而定 (由 Microsoft 管理或客戶管理)，您對實作之後的 Microsoft Azure Rights Management (Azure RMS) 租用戶金鑰會有不同程度的控制與責任。

當您管理自己的租用戶金鑰時，這通常稱為整合您自己的金鑰 (BYOK)。 如需此案例及如何在這兩種租用戶金鑰拓撲之中做選擇的詳細資訊，請參閱＜[規劃及實作 Azure Rights Management 租用戶金鑰](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md)＞。

下表視您為 Azure RMS 租用戶金鑰選擇的拓撲而定，指出您可以執行的作業。

|生命週期作業|由 Microsoft 管理 (預設)|由客戶管理 (BYOK)|
|----------|-----------------------|----------------|
|撤銷租用戶金鑰|否 (自動)|否 (自動)|
|更換租用戶金鑰|是|是|
|備份和復原租用戶金鑰|否|是|
|匯出租用戶金鑰|是|否|
|漏洞應變|是|是|
識別您已實作的拓撲之後，請參閱下列其中一節，以了解對 Azure RMS 租用戶金鑰執行這些作業的詳細資訊。

## <a name="BKMK_MSManagedOperations"></a>由 Mcrosoft 管理：租用戶金鑰生命週期作業
如果 Microsoft 為您管理 Azure Rights Management 的租用戶金鑰 (預設)，請參閱下列各節，以了解與此拓撲有關的生命週期作業的詳細資訊：

-   [撤銷租用戶金鑰](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSRevoke)

-   [更換租用戶金鑰](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSRekey)

-   [備份和復原租用戶金鑰](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSBackup)

-   [匯出租用戶金鑰](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSExport)

-   [漏洞應變](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSBreach)

### <a name="BKMK_MSRevoke"></a>撤銷租用戶金鑰
當您取消訂閱 Azure RMS 時，Azure RMS 會停止使用您的租用戶金鑰，您不必採取任何動作。

### <a name="BKMK_MSRekey"></a>更換租用戶金鑰
更換金鑰又稱為輪換金鑰。 除非真有必要，請不要更換租用戶金鑰。 舊版的用戶端 (例如 Office 2010) 無法正確處理金鑰變更。 在此情況下，您必須使用群組原則或同等的機制來清除電腦上的 RMS 狀態。 不過，有些法律事件可能迫使您不得不更換租用戶金鑰。 例如：

-   您的公司分拆成兩家以上的公司。 當您更換租用戶金鑰時，新公司將無法存取您的員工所發佈的新內容。 只要他們有一份舊的租用戶金鑰，就可以存取舊的內容。

-   您認為租用戶金鑰的正本 (您擁有的副本) 被盜。

您可以連絡 Microsoft 客戶支援服務 (CSS) 並證明您是租用戶管理員，以更換租用戶金鑰。

當您更換租用戶金鑰時，新的內容會以新的租用戶金鑰來保護。 這是分階段逐步進行，所以在一段期間內，有些新的內容會持續以舊的租用戶金鑰來保護。 先前保護的內容仍然是以舊的租用戶金鑰來保護。 為了支援此案例，Azure RMS 會保留舊的租用戶金鑰，所以可以為舊的內容發出授權。

### <a name="BKMK_MSBackup"></a>備份和復原租用戶金鑰
Microsoft 會負責備份您的租用戶金鑰，您不必採取任何動作。

### <a name="BKMK_MSExport"></a>匯出租用戶金鑰
您可以依照下列這三個步驟的指示，匯出您的 Azure RMS 組態和租用戶金鑰：

##### 步驟 1：起始匯出

-   若要這樣做，請連絡 Microsoft 客戶服務支援 (CSS)。 您必須證明您是 Azure RMS 租用戶的管理員。

##### 步驟 2：等待驗證

-   Microsoft 會驗證您提出發放 RMS 租用戶金鑰的要求是合法。 此程序最多需要 3 週的時間。

##### 步驟 3：從 CSS 取得金鑰指示

-   Microsoft 客戶支援服務 (CSS) 會在密碼保護的檔案 (副檔名為 .tpd) 中將 Azure RMS 組態和租用戶金鑰加密，然後傳送給您。 為了這樣做，CSS 會先透過電子郵件傳送工具給您 (也就是起始匯出的人)。 您必須從命令提示字元中執行此工具，如下所示：

    ```
    AadrmTpd.exe -createkey
    ```
    這樣會產生 RSA 金鑰組，並以檔案分成公開和私密兩部分，儲存在目前的資料夾中。 例如：**PublicKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt** 及 **PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt**。

    回覆 CSS 寄來的電子郵件，並附上檔名開頭為 **PublicKey** 的檔案。 之後，CSS 會傳送 TPD 檔案給您做為以 RSA 金鑰加密的 .xml 檔案。 將這個檔案複製到您一開始執行 AadrmTpd 工具時的相同資料夾，並使用以 **PrivateKey** 開頭的檔案以及來自 CSS 的檔案，再次執行工具。 例如：

    ```
    AadrmTpd.exe -key PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt -target TPD-77172C7B-8E21-48B7-9854-7A4CEAC474D0.xml
    ```
    此命令應該會輸出兩個檔案：其中一個包含受密碼保護的 TPD 的純文字密碼，另一個是受密碼保護的 TPD 本身。 為了交互參照，兩者的 GUID 應該與您執行 AadrmTpd.exe -createkey 命令時的公開和私密金鑰檔案相同：

    -   Password-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt

    -   ExportedTPD-FA29D0FE-5049-4C8E-931B-96C6152B0441.xml

    請備份這些檔案並妥善保管，以確保您能夠繼續解密以這個租用戶金鑰所保護的內容。 此外，如果是要移轉至 AD RMS，您可以將此 TPD 檔案 (以 **ExportedTDP** 開頭的檔案) 匯入到 AD RMS 伺服器。

##### 步驟 4：繼續：保護租用戶金鑰

-   收到租用戶金鑰之後，請安全地保管，因為如果某人取得金鑰，他就可以將所有使用此金鑰保護的文件解密。

    如果您因為不想再使用 Azure RMS 而匯出租用戶金鑰，則最佳做法就是立即停用 RMS 租用戶。 收到租用戶金鑰之後，請立即這樣做，切勿拖延，因為這項預防措施可將租用戶金鑰誤入他人之手的後果降到最低。 如需相關指示，請參閱＜[解除委任並停用 Azure Rights Management](../Topic/Decommissioning_and_Deactivating_Azure_Rights_Management.md)＞。

### <a name="BKMK_MSBreach"></a>漏洞應變
安全性系統不論多麼堅固，不可能完美到沒有任何漏洞應變程序。 租用戶金鑰可能已外洩或遭竊。 即使受到嚴密保護，最新一代 HSM 技術或目前的金鑰長度和演算法仍可能有弱點。

Microsoft 有專屬團隊負責對產品與服務中的安全性事件做出應變。 每當有可靠的報告指出有事件發生，此團隊就會立即介入來調查範圍、根本原因及防護措施。 如果此事件影響到您的資產，Microsoft 會以您訂閱時所提供的地址，以電子郵件來通知您的 Azure RMS 租用戶管理員。

如果發生漏洞，您或 Microsoft 可採取的最佳行動取決於漏洞的範圍；Microsoft 會與您一起完成此過程。 下表顯示一些常見的情況和可能的反應，但確切的反應取決於調查期間揭露的所有資訊。

|事件描述|可能的反應|
|--------|---------|
|租用戶金鑰外洩。|更換租用戶金鑰。 請參閱本主題的＜[更換租用戶金鑰](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_MSRekey)＞一節。|
|未獲授權的人或惡意程式碼可能取得權限來使用您的租用戶金鑰，但金鑰本身並未外洩。|更換租用戶金鑰在此無濟於事，必須分析根本原因。 如果是程序或軟體的錯誤導致未獲授權的人取得存取權，則必須解決這種情況。|
|經由運算可找出 RSA 演算法、金鑰長度或暴力密碼破解攻擊的弱點。|Microsoft 必須更新 Azure RMS 來支援更強韌的新演算法和更長的金鑰長度，並指示所有客戶更新其租用戶金鑰。|

## <a name="BKMK_BYOKManagedOperations"></a>由客戶管理：租用戶金鑰生命週期作業
如果您自行管理 Azure Rights Management 的租用戶金鑰 (整合您自己的金鑰案例，簡稱為 BYOK)，請參閱下列各節，以了解與此拓撲有關的生命週期作業的詳細資訊：

-   [撤銷租用戶金鑰](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKRevoke)

-   [更換租用戶金鑰](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKRekey)

-   [備份和復原租用戶金鑰](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKBackup)

-   [匯出租用戶金鑰](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKExport)

-   [漏洞應變](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKBreach)

### <a name="BKMK_BYOKRevoke"></a>撤銷租用戶金鑰
當您取消訂閱 Azure RMS 時，Azure RMS 會停止使用您的租用戶金鑰，您不必採取任何動作。

### <a name="BKMK_BYOKRekey"></a>更換租用戶金鑰
更換金鑰又稱為輪換金鑰。 除非真有必要，請不要更換租用戶金鑰。 舊版的用戶端 (例如 Office 2010) 無法正確處理金鑰變更。 在此情況下，您必須使用群組原則或同等的機制來清除電腦上的 RMS 狀態。 不過，有些法律事件可能迫使您不得不更換租用戶金鑰。 例如：

-   您的公司分拆成兩家以上的公司。 當您更換租用戶金鑰時，新公司將無法存取您的員工所發佈的新內容。 只要他們有一份舊的租用戶金鑰，就可以存取舊的內容。

-   您認為租用戶金鑰的正本 (您擁有的副本) 被盜。

當您更換租用戶金鑰時，新的內容會以新的租用戶金鑰來保護。 這是分階段逐步進行，所以在一段期間內，有些新的內容會持續以舊的租用戶金鑰來保護。 先前保護的內容仍然是以舊的租用戶金鑰來保護。 為了支援此案例，Azure RMS 會保留舊的租用戶金鑰，所以可以為舊的內容發出授權。

若要重設租用戶金鑰，請透過網際網路或親自產生並建立新的金鑰，請使用＜[實作整合您自己的金鑰 (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK)＞主題的＜[規劃及實作 Azure Rights Management 租用戶金鑰](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md)＞一節中的程序來進行。

### <a name="BKMK_BYOKBackup"></a>備份和復原租用戶金鑰
您負責備份租用戶金鑰。 如果是在 Thales HSM 中產生租用戶金鑰，若要備份金鑰，只需要備份信號化金鑰檔案、園地檔案及系統管理員卡。

如果您依照＜[實作整合您自己的金鑰 (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK)＞主題的＜[規劃及實作 Azure Rights Management 租用戶金鑰](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md)＞一節中的程序來傳輸金鑰，Azure RMS 會保留信號化金鑰檔案，以因應任何 Azure RMS 節點發生故障的情況。 然而，這並不算是完整備份。 例如，若您還是可能需要在 Thales HSM 以外使用金鑰的純文字副本，則 Azure RMS 無法擷取它，因為它只有無法復原的副本。

### <a name="BKMK_BYOKExport"></a>匯出租用戶金鑰
如果您使用 BYOK，您無法從 Azure RMS 匯出租用戶金鑰。 Azure RMS 中是無法復原的副本。 如果您想要刪除這個金鑰不再使用，請連絡 Microsoft 客戶服務支援 (CSS)。

### <a name="BKMK_BYOKBreach"></a>漏洞應變
安全性系統不論多麼堅固，不可能完美到沒有任何漏洞應變程序。 租用戶金鑰可能已外洩或遭竊。 即使受到嚴密保護，最新一代 HSM 技術或目前的金鑰長度和演算法仍可能有弱點。

Microsoft 有專屬團隊負責對產品與服務中的安全性事件做出應變。 每當有可靠的報告指出有事件發生，此團隊就會立即介入來調查範圍、根本原因及防護措施。 如果此事件影響到您的資產，Microsoft 會以您訂閱時所提供的地址，以電子郵件來通知您的 Azure RMS 租用戶管理員。

如果發生漏洞，您或 Microsoft 可採取的最佳行動取決於漏洞的範圍；Microsoft 會與您一起完成此過程。 下表顯示一些常見的情況和可能的反應，但確切的反應取決於調查期間揭露的所有資訊。

|事件描述|可能的反應|
|--------|---------|
|租用戶金鑰外洩。|更換租用戶金鑰。 請參閱本主題的＜[更換租用戶金鑰](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_BYOKRekey)＞一節。|
|未獲授權的人或惡意程式碼可能取得權限來使用您的租用戶金鑰，但金鑰本身並未外洩。|更換租用戶金鑰在此無濟於事，必須分析根本原因。 如果是程序或軟體的錯誤導致未獲授權的人取得存取權，則必須解決這種情況。|
|最新一代 HSM 技術中發現的弱點。|Microsoft 必須更新 HSM。 如果確信弱點已暴露金鑰，則 Microsoft 會指示所有客戶更新其租用戶金鑰。|
|經由運算可找出 RSA 演算法、金鑰長度或暴力密碼破解攻擊的弱點。|Microsoft 必須更新 Azure RMS 來支援更強韌的新演算法和更長的金鑰長度，並指示所有客戶更新其租用戶金鑰。|

## 請參閱
[使用 Azure Rights Management](../Topic/Using_Azure_Rights_Management.md)

