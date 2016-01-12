---
description: na
keywords: na
title: Activating Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f8707e01-b239-4d1a-a1ea-0d1cf9a8d214
---
# 啟用 Azure Rights Management
當您啟用 [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS) 時，您的組織就可以開始使用支援資訊保護解決方案的應用程式與服務保護重要資料。 系統管理員也可以管理與監控您的組織所擁有的受保護檔案及電子郵件。 您必須先啟動 [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)]，才能開始在 Office、SharePoint 和 Exchange 中使用資訊版權管理 (IRM) 功能，並保護任何敏感或機密檔案。

如果您想要在啟動服務之前先深入了解 Azure Rights Management，例如，它可以解決哪些商務問題、幾個一般使用案例，及運作方式，請參閱＜[什麼是 Azure Rights Management？](../Topic/What_is_Azure_Rights_Management_.md)＞

> [!IMPORTANT]
> 啟動 [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] 之前，請確定您的組織具有包含 [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] 服務的服務方案。 如果沒有，您將無法啟動 Azure RMS。
> 
> 如需詳細資訊，請參閱[Azure Rights Management 的需求](../Topic/Requirements_for_Azure_Rights_Management.md) 主題中的[支援 Azure RMS 的雲端訂閱](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions)一節。

啟動 Azure RMS 之後，您組織中的所有使用者都可以在他們的檔案上套用資訊保護，且所有使用者都可以開啟 (使用) 受 Azure RMS 保護的檔案。 不過，如果您要的話，您可以限制誰可以套用資訊保護，方法是在分階段部署中使用登入控制項。 如需詳細資訊，請參閱本主題中的＜[設定分階段部署的登入控制項](../Topic/Activating_Azure_Rights_Management.md#BKMK_OnboardingControls)＞一節。

## 啟用 Rights Management
使用下列其中一個程序來啟動 [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)]。

> [!TIP]
> 您也可以使用 Windows PowerShell Cmdlet [Enable-Aadrm](http://msdn.microsoft.com/library/windowsazure/dn629412.aspx) 來啟動 [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)]。

#### 若要從 Office 365 系統管理中心啟動 Rights Management

1.  在您註冊 Office 365 方案 (包含 Rights Management) 之後，[使用工作或學校帳戶登入 Office 365](https://portal.office.com/)，也就是您的 Office 365 部署的系統管理員。

2.  如果 Office 365 系統管理中心未自動顯示，請選取左上角的應用程式啟動器圖示，並選擇 **[管理員]**。 只有 Office 365 管理員才會看到 **[管理員]** 方塊。

    > [!TIP]
    > 如需系統管理中心說明，請參閱 [關於 Office 365 系統管理中心 - 管理員說明](https://support.office.com/article/About-the-Office-365-admin-center-Admin-Help-58537702-d421-4d02-8141-e128e3703547)。

3.  展開左窗格中的 **[服務設定]**。

4.  按一下 **[Rights Management]**。

    > [!NOTE]
    > 若未看到此選項，則可能是因為您的服務方案或產品版本無法支援 Rights Management，或它尚未升級到支援 Rights Management。
    > 
    > 使用＜[Azure Rights Management 的需求](../Topic/Requirements_for_Azure_Rights_Management.md)＞主題中的＜[支援 Azure RMS 的雲端訂閱](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions)＞一節的資訊來確認支援。 如果支援您的服務方案或產品版本，但您看不到 Rights Management 選項，則可能是因為尚未升級服務。 如需這個問題的說明，請將電子郵件訊息傳送至 [askipteam](mailto:askipteam@microsoft.com?subject=I%20cannot%20activate%20RMS)。

5.  在 **[RIGHTS MANAGEMENT]** 頁面上，按一下 **[管理]**。

6.  在 **[RIGHTS MANAGEMENT]** 頁面上，按一下 **[啟動]**。

7.  出現 **[是否要啟動 Rights Management?]** 提示時，按一下 **[啟動]**。

現在應該會顯示 **[Rights Management 已啟動]** 及用來停用的選項。

#### 若要從 Azure 傳統入口網站啟動 Rights Management

1.  在您註冊 Azure 帳戶之後，[登入 Azure 傳統入口網站](http://go.microsoft.com/fwlink/p/?LinkID=275081)。

2.  在左窗格中，按一下 **[ACTIVE DIRECTORY]**。

3.  從 **[active directory]** 頁面中，按一下 **[RIGHTS MANAGEMENT]**。

4.  選取要為 [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] 管理的目錄，按一下 **[啟動]**，然後確認您的動作。

    > [!NOTE]
    > 如果出現啟動錯誤，則可能是因為您的服務方案或產品版本無法支援 [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)]。
    > 
    > 使用＜[Azure Rights Management 的需求](../Topic/Requirements_for_Azure_Rights_Management.md)＞主題中的＜[支援 Azure RMS 的雲端訂閱](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedSubscriptions)＞一節的資訊來確認 RMS 支援。 如需這個問題的說明，請將電子郵件訊息傳送至 [askipteam](mailto:askipteam?subject=I%20cannot%20activate%20RMS)。

**[RIGHTS MANAGEMENT 狀態]** 現在應該會顯示為 **[作用中]**，且 **[啟動]** 選項會取代為 **[停用]**。

### Azure 傳統入口網站中的 Rights Management 狀態值和說明
除了 **[使用中]** 狀態 (指出已啟用 Rights Management 服務並準備好可供使用) 之外，您可能也會看到 **[非使用中]**、**[無法使用]** 或 **[未授權]**。

|狀態值|說明|
|-------|------|
|**作用中**|已啟用 [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] 並準備好可供使用。|
|**非作用中**|已停用 [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)]，而且必須在組織可以保護檔案之前啟動。|
|**無法使用**|已關閉 [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] 服務。 請稍後再試一次。|
|**未授權**|您沒有檢視 [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] 服務狀態的權限。 例如，已鎖定您的帳戶，或您不是所選取租用戶的全域管理員。|

## <a name="BKMK_OnboardingControls"></a>設定分階段部署的登入控制項
如果您不想要讓所有使用者能夠藉由使用 Azure RMS 以立即保護檔案，您可以設定使用者上線控制，方法是使用 [Set-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857521.aspx) Windows PowerShell 命令。 您可以在啟動 Azure RMS 前後執行此命令。

> [!IMPORTANT]
> 若要使用此命令，您至少必須有 **2.1.0.0** 版的 [Azure RMS Windows PowerShell 模組](http://go.microsoft.com/fwlink/?LinkId=257721)。
> 
> 若要檢查您已安裝的版本，請執行：**(Get-Module aadrm –ListAvailable).Version**

例如，如果基於測試目的，您一開始只希望 “IT department” 群組中的管理員 (包含 fbb99ded-32a0-45f1-b038-38b519009503 物件識別碼) 能夠保護內容，請使用下列命令：

```
Set-AadrmOnboardingControlPolicy – SecurityGroupObjectId fbb99ded-32a0-45f1-b038-38b519009503
```
請注意，您必須針對此組態選項指定一個群組；您無法指定個人使用者。

或者，如果您要確保只有已正確授權使用 Azure RMS 的使用者才能保護內容：

```
Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $true
```
當您使用這些登入控制項時，組織中的所有使用者一律可以使用受部分使用者保護的受保護內容，但他們無法從用戶端應用程式中自行套用資訊保護。 例如，他們無法在 Office 用戶端中看到啟動 Azure RMS 時會自動發佈的預設範本，或您所設定的自訂範本。  伺服器端應用程式 (例如 Exchange) 可針對 RMS 整合實作個別使用者的控制，以達成相同結果。

## 後續步驟
現在您已為您的組織啟動 [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)]，請使用[Azure Rights Management 部署藍圖](../Topic/Azure_Rights_Management_Deployment_Roadmap.md)檢查將 [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] 轉出給使用者和系統管理員之前，是否還需要執行其他設定步驟。 例如，您可能想要使用[自訂範本](http://technet.microsoft.com/library/dn642472.aspx)讓使用者更容易將資訊保護套用至檔案，藉由安裝 [RMS 連接器](http://technet.microsoft.com/library/dn375964.aspx)來連接您的內部部署伺服器以使用 [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)]，並且部署 [Rights Management 共用應用程式](http://technet.microsoft.com/library/jj585031.aspx)，支援保護所有裝置上的所有檔案類型。 Office 服務 (例如 Exchange Online 及and SharePoint Online) 都需要先進行其他設定，才能使用其資訊版權管理 (IRM) 功能。 然而，若不需要執行其他設定步驟，請參閱[使用 Azure Rights Management](../Topic/Using_Azure_Rights_Management.md) 取得操作指示，以支援組織的成功部署。

如需有關應用程式如何使用 [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] 的詳細資訊，請參閱＜[應用程式如何支援 Azure Rights Management](../Topic/How_Applications_Support_Azure_Rights_Management.md)＞。

## 請參閱
[設定 Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

