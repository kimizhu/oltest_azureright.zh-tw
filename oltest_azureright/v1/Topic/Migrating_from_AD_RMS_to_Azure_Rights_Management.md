---
description: na
keywords: na
title: Migrating from AD RMS to Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 828cf1f7-d0e7-4edf-8525-91896dbe3172
---
# 從 AD RMS 移轉至 Azure Rights Management
使用下列一組指令來將您的 Active Directory Rights Management Services (AD RMS) 部署移轉至 Azure Rights Management (Azure RMS)。 移轉之後，使用者仍然可以存取您組織使用 AD RMS 保護的文件及電子郵件訊息，而之後將使用 Azure RMS 重新保護內容。

不確定您的組織是否適合 AD RMS 移轉？

-   如需關於 Azure RMS 的介紹、Azure RMS 可解決的業務問題、系統管理員和使用者使用時的呈現方式，以及運作方式﹐請參閱[什麼是 Azure Rights Management？](../Topic/What_is_Azure_Rights_Management_.md)

-   關於 Azure RMS 與 AD RMS 的比較，請參閱[比較 Azure Rights Management 與 AD RMS](../Topic/Comparing_Azure_Rights_Management_and_AD_RMS.md)。

## 從 AD RMS 移轉至 Azure RMS 的必要條件
請確定您符合下列必要條件且了解任何限制，再開始移轉至 Azure RMS。

|需求|詳細資訊|
|------|--------|
|支援的 RMS 部署|從 Windows Server 2008 到 Windows Server 2012 R2 的所有 AD RMS 版本都支援移轉至 Azure RMS：<br /><br />-   Windows Server 2008 (x86 或 x64)<br />-   Windows Server 2008 R2 (x64)<br />-   Windows Server 2012 (x64)<br />-   Windows Server 2012 R2 (x64) **Note:** 如果您是在 Windows Server 2003 上執行 Windows RMS，這個版本的作業系統將在 2015年期間不再提供支援。 您可以將這個版本的 RMS 移轉至 Azure RMS，但只在仍支援作業系統時，才支援此程序。 因應措施是將信任的發佈網域 (TPD) 匯入至支援的 AD RMS 版本，然後在不使用 RMS 1.0 相容性選項的情況下重新匯入 TPD。 如需 TPD 的詳細資訊，請參閱＜[信任的發行網域](http://technet.microsoft.com/library/dd996639%28v=ws.10%29.aspx)＞<br />支援所有有效的 AD RMS 拓撲：<br /><br />-   單一樹系、單一 RMS 叢集<br />-   單一樹系、多個僅授權 RMS 叢集<br />-   多個樹系、多個 RMS 叢集 **Note:** 多個 RMS 叢集預設會移轉至單一 Azure RMS 租用戶。 如果您想要不同的 RMS 租用戶，則必須將它們視為不同的移轉。 一個 RMS 叢集的金鑰不能匯入至多個 Azure RMS 租用戶。|
|執行 Azure RMS 的所有需求 (包括 Azure RMS 租用戶) (未啟動)|請參閱＜[Azure Rights Management 的需求](../Topic/Requirements_for_Azure_Rights_Management.md)＞。<br /><br />雖然您必須有 Azure RMS 租用戶，才能從 AD RMS 進行移轉，但是我們建議在移轉之前，請先不要啟動 Rights Management Service。 從 AD RMS 匯出金鑰和範本並將它們匯入至 Azure RMS 之後，移轉程序即會包括此步驟。 不過，如果已啟用 Azure RMS，仍然可以從 AD RMS 移轉。|
|Azure RMS 的準備：<br /><br />-   內部部署目錄與 Azure Active Directory 之間的目錄同步作業<br />-   Azure Active Directory 中擁有郵件功能的群組|請參閱＜[準備 Azure Rights Management](../Topic/Preparing_for_Azure_Rights_Management.md)＞。|
|如果您曾使用 Exchange Server 的資訊版權管理 (IRM) 功能 (如傳輸規則和 Outlook Web Access) 或 SharePoint Server 來搭配 AD RMS：<br /><br />-   規劃 IRM 無法在這些伺服器上使用的一段短期間|移轉之後，您可以繼續搭配使用這些伺服器上的 IRM 與 Azure RMS。 不過，其中一個移轉步驟是暫時停用 IRM 服務、安裝和設定連接器、重新設定伺服器，然後重新啟用 IRM。<br /><br />這是移轉程序期間唯一發生的服務中斷。|
限制：

-   雖然移轉程序支援將伺服器授權憑證 (SLC) 金鑰移轉至 Azure RMS 的硬體安全性模組 (HSM)，但是 Exchange Online 目前不支援這項組態。如果在移轉至 Azure RMS 之後，您想要完整 IRM 功能與 Exchange Online 搭配，則您的 Azure RMS 租用戶金鑰必須由 [Microsoft 管理](http://technet.microsoft.com/library/dn440580.aspx)。或者，當 Azure RMS 租用戶由您管理時，您可以在 Exchange Online 中執行功能精簡的 IRM (BYOK)。如需搭配使用 Exchange Online 與 Azure RMS 的詳細資訊，請參閱這些指示中的 [Step 6. Configure IRM integration for Exchange Online](#BKMK_Step6Migration)。

-   如果 Azure RMS 不支援您的軟體和用戶端，則軟體和用戶端無法保護或使用 Azure RMS 所保護的內容。 請務必檢查＜[Azure Rights Management 的需求](../Topic/Requirements_for_Azure_Rights_Management.md)＞主題中的支援的應用程式和用戶端一節。

-   如果您將內部部署金鑰匯入至 Azure RMS，做為保存的金鑰 (您未將 TPD 設定為在匯入程序期間作用中)，而且您批次移轉使用者，以進行分段移轉，則已移轉的使用者新保護的內容無法供仍留在 AD RMS 的使用者存取。 在此案例中，請盡可能保持簡短的移轉時間，並以邏輯批次方式移轉使用者，以便如果他們彼此合作，可以一起移轉它們。

    當您將 TPD 設定為在匯入期間作用中時，這項限制不適用，因為所有使用者將使用相同金鑰來保護內容。 我們建議此組態，因為它可讓您獨立並依自己的步調移轉所有使用者。

-   如果您與外部合作夥伴合作 (如藉由使用信任的使用者網域或同盟)，他們也必須在您移轉至 Azure RMS 時同時移轉，抑或是在您移轉後儘快移轉。 若要繼續存取組織先前使用 AD RMS 保護的內容，他們必須進行用戶端組態變更 (類似您所做的變更)，並包括在這份文件內。

    由於合作夥伴之間的組態可能不盡相同，因此本文件不探討本次重新組態的確切指示。 如需協助，請連絡 Microsoft 客戶支援服務 (CSS)。

## 從 AD RMS 移轉至 Azure RMS 的步驟

|移轉步驟|詳細資訊|
|--------|--------|
|**1.下載 Azure RMS Management 管理工具**|如需相關指示，請參閱＜[Step 1: Download the Azure Rights Management Administration Tool](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step1Migration)＞。|
|**2.從 AD RMS 匯出組態資料，並將它匯入至 Azure RMS**|您可以將組態資料 (金鑰、範本、URL) 從 AD RMS 匯出至 XML 檔案，然後再使用 Import-AadrmTpd Windows PowerShell Cmdlet 將該檔案上傳至 Azure RMS。 可能還需要額外的步驟 (視 AD RMS 金鑰組態而定)：<br /><br />-   軟體保護的金鑰移轉至軟體保護的金鑰：AD RMS 中集中管理的密碼金鑰到 Microsoft 管理的 Azure RMS 租用戶金鑰。 這是最簡單的移轉路徑，而且不需要任何額外的步驟。<br />-   HSM 保護的金鑰移轉至 HSM 保護的金鑰：HSM for AD RMS儲存的金鑰到客戶管理的 Azure RMS 租用戶金鑰 (「整合您自己的金鑰」或 BYOK 案例)。 這需要額外的步驟，才能將金鑰從內部部署 Thales HSM 傳輸至 Azure RMS HSM。<br />-   軟體保護的金鑰移轉至 HSM 保護的金鑰：AD RMS 中集中管理的密碼金鑰到客戶管理的 Azure RMS 租用戶金鑰 (「自備您自己的金鑰」或 BYOK 案例)。 這需要進行最多的組態，因為您必須先擷取您的軟體金鑰並將它匯入至內部部署 HSM，然後再執行其他步驟，將金鑰從內部部署 Thales HSM 傳輸至 Azure RMS HSM。<br /><br />如需相關指示，請參閱＜[Step 2. Export configuration data from AD RMS and import it to Azure RMS](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step2Migration)＞。|
|**3.啟動您的 RMS 租用戶**|可能的話，請在匯入程序之後執行此步驟，而不是在之前執行。<br /><br />如需詳細資訊和指示，請參閱＜[Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration)＞。|
|**4.設定匯入的範本**|匯入權限原則範本時，會封存其狀態。 如果您想要使用者能夠看到並使用它們，則必須在 Azure 傳統入口網站中將範本狀態變更為已發佈。<br /><br />如需相關指示，請參閱＜[Step 4. Configure imported templates](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step4Migration)＞。|
|**5.重新設定用戶端使用 Azure RMS**|現有的 Windows 電腦必須重新設定為使用 Azure RMS 服務，而不是 AD RMS。 如果您在執行 AD RMS 時與您組織中的電腦以及合作夥伴組織中的電腦共同作業，則此步驟適用於這些電腦。<br /><br />此外，如果您已部署[行動裝置延伸模組](http://technet.microsoft.com/library/dn673574.aspx)來支援 iOS 行動電話和 iPad、Android 行動電話和平板電腦、Windows 行動電話及 Mac 電腦，必須移除 DNS 中重新導向這些用戶端以使用 AD RMS 的 SRV 記錄。<br /><br />如需相關指示，請參閱＜[Step 5. Reconfigure clients to use Azure RMS](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step5Migration)＞。|
|**6.設定 IRM 與 Exchange Online 整合**|如果想要搭配使用 Exchange Online 與 Azure RMS，則需要此步驟。<br /><br />如需相關指示，請參閱＜[Step 6. Configure IRM integration for Exchange Online](#BKMK_Step6Migration)＞。|
|**7.部署 RMS 連接器**|如果您想要搭配使用下列任何內部部署服務與 Azure RMS，則需要這個步驟：<br /><br />-   Exchange Server (如傳輸規則和 Outlook Web Access)<br />-   SharePoint Server<br />-   執行檔案分類基礎結構的 Windows Server<br /><br />如需相關指示，請參閱＜[步驟 7. 解除委任 AD RMS](#BKMK_Step7Migration)＞。|
|**8.解除委任 AD RMS**|確認所有用戶端都使用 Azure RMS 而且不再存取 AD RMS 伺服器時，即可解除委任 AD RMS 部署。<br /><br />如需相關指示，請參閱＜[步驟 8. 重新設定 Azure RMS 租用戶金鑰](#BKMK_Step8Migration)＞。|
|**9.重新設定 Azure RMS 租用戶金鑰**|如果您在移轉之前未執行加密模式 2，則需要這個步驟，而且，雖然這個步驟對於所有移轉都是選擇性的，但是建議使用，以協助保護您 Azure RMS 租用戶金鑰的安全性。<br /><br />如需相關指示，請參閱＜[Step 9. Re-key your Azure RMS tenant key](#BKMK_Step9Migration)＞。|

### <a name="BKMK_Step1Migration"></a>步驟 1：下載 Azure Rights Management 管理工具
移至 Microsoft 下載中心並下載 [Azure Rights Management 管理工具](http://go.microsoft.com/fwlink/?LinkId=257721)，其中包含適用於 Windows PowerShell 的 Azure RMS 管理模組。

### <a name="BKMK_Step2Migration"></a>步驟 2： 從 AD RMS 匯出組態資料，並將它匯入至 Azure RMS
這個步驟是兩部分的程序：

1.  將信任的發佈網域 (TPD) 匯出至 .xml 檔案，以從 AD RMS 匯出組態資料。 所有移轉的這個程序都相同。

2.  將組態資料匯入至 Azure RMS。 根據目前的 AD RMS 部署組態以及 Azure RMS 租用戶金鑰的慣用拓撲，此步驟會有不同的程序。

#### 從 AD RMS 匯出組態資料
針對具有您組織受保護內容的所有信任的發佈網域，在所有 AD RMS 叢集上執行下列程序。 您不需要在僅授權叢集上執行此程序。

> [!NOTE]
> 如果您使用 Windows Server 2003 Rights Management 而非這些指示，請依照＜[在不同的基礎結構中從 Windows RMS 移轉至 AD RMS](http://technet.microsoft.com/library/jj835767%28v=ws.10%29.aspx)＞主題的[匯出 SLC、TUD、TPD 和 RMS 私密金鑰](http://technet.microsoft.com/library/jj835767%28v=ws.10%29.aspx)程序。

###### 匯出組態資料 (信任的發佈網域資訊)

1.  以具有 AD RMS 系統管理權限的使用者身分，登入 AD RMS 叢集。

2.  從 AD RMS 管理主控台 ([**Active Directory Rights Management Service**])，依序展開 AD RMS 叢集名稱和 [**信任原則**]，然後按一下 [**信任的發佈網域**]。

3.  在結果窗格中，選取信任的發佈網域，然後按一下 [動作] 窗格中的 [**匯出信任的發佈網域**]。

4.  在 [**匯出信任的發佈網域**] 對話方塊中：

    -   按一下 [**另存新檔**]，並儲存至您所選擇的路徑和檔案名稱。 請務必指定 **.xml** 做為副檔名 (這不會自動予以附加)。

    -   指定並確認增強式密碼。 請記住這個密碼，因為您稍後將組態資料匯入至 Azure RMS 時會需要它。

    -   請不要選取此核取方塊來儲存 RMS 1.0 版格式的信任的網域檔案。

匯出所有信任的發佈網域之後，即可開始將此資料匯入至 Azure RMS 的程序。

#### 將組態資料匯入至 Azure RMS
此步驟的確切程序取決於目前的 AD RMS 部署組態以及 Azure RMS 租用戶金鑰的慣用拓撲。

目前的 AD RMS 部署會針對您的伺服器授權人憑證 (SLC) 金鑰使用下列其中一個組態：

-   AD RMS 資料庫中的密碼保護。 這是預設組態。

-   使用 Thales 硬體安全性模組 (HSM) 的 HSM 保護。

-   使用非 Thales 供應商之硬體安全性模組 (HSM) 的 HSM 保護。

-   使用外部加密提供者所保護的密碼。

> [!NOTE]
> 如需搭配使用硬體安全性模組與 AD RMS 的詳細資訊，請參閱[搭配使用 AD RMS 與硬體安全性模組](http://technet.microsoft.com/library/jj651024.aspx)。

兩個 Azure RMS 租用戶金鑰拓撲選項如下：Microsoft 管理您的租用戶金鑰 (**由 Microsoft 管理**) 或您管理您的租用戶金鑰 (**由客戶管理**)。 管理您自己的 Azure RMS 租用戶金鑰時，有時稱為「整合您自己的金鑰」(BYOK)，而且需要 Thales 的硬體安全性模組 (HSM)。 如需詳細資訊，請參閱[規劃及實作 Azure Rights Management 租用戶金鑰](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md)主題中的[選擇您的租用戶金鑰拓撲：由 Microsoft 管理 (預設) 或由您管理 (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ChooseTenantKey)一節。

> [!IMPORTANT]
> Exchange Online 目前與 Azure RMS BYOK 不相容。  如果您想要在移轉之後使用 BYOK，並計畫使用 Exchange Online，請確定您了解這項組態如何減少 Exchange online 的 IRM 功能。 檢閱＜[規劃及實作 Azure Rights Management 租用戶金鑰](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md)＞主題中＜[BYOK 定價和限制](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing)＞一節中的資訊，以協助您選擇最佳的 Azure RMS 租用戶金鑰拓撲進行移轉。

請使用下表來識別要用於移轉的程序。 不支援未列出的組合。

|目前的 AD RMS 部署|選擇的 Azure RMS 租用戶金鑰拓撲|移轉指示|
|-----------------|-------------------------|--------|
|AD RMS 資料庫中的密碼保護|由 Mcrosoft 管理|請參閱這個資料表後面的＜**軟體保護的金鑰移轉至軟體保護的金鑰**＞程序。<br /><br />這是最簡單的移轉路徑，而且您只需要將組態資料傳輸至 Azure RMS。|
|使用 Thales nShield 硬體安全性模組 (HSM) 的 HSM 保護|由客戶管理 (BYOK)|請參閱這個資料表後面的＜**HSM 保護的金鑰移轉至 HSM 保護的金鑰**＞程序。<br /><br />這需要 BYOK 工具組和兩組步驟，以將金鑰從內部部署 HSM 傳輸至 Azure RMS HSM，然後再將組態資料傳輸至 Azure RMS。|
|AD RMS 資料庫中的密碼保護|由客戶管理 (BYOK)|請參閱這個資料表後面的＜**軟體保護的金鑰移轉至 HSM 保護的金鑰**＞程序。<br /><br />這需要 BYOK 工具組和三組步驟，先擷取您的軟體金鑰並將它匯入至內部部署 HSM，然後再將金鑰從內部部署 HSM 傳輸至 Azure RMS HSM，最後再將組態資料傳輸至 Azure RMS。|
|使用非 Thales 供應商之硬體安全性模組 (HSM) 的 HSM 保護|由客戶管理 (BYOK)|如需如何將金鑰從此 HSM 傳輸至 Thales nShield 硬體安全性模組 (HSM)的指示，請連絡 HSM 的供應商。 然後，遵循這個資料表後面的＜**HSM 保護的金鑰移轉至 HSM 保護的金鑰**＞程序的指示。|
|使用外部加密提供者所保護的密碼|由客戶管理 (BYOK)|如需如何將金鑰傳輸至 Thales nShield 硬體安全性模組 (HSM)的指示，請連絡加密提供者的供應商。 然後，遵循這個資料表後面的＜**HSM 保護的金鑰移轉至 HSM 保護的金鑰**＞程序的指示。|
啟動這些程序之前，請確定您可以存取先前在匯出信任的發佈網域時所建立的 .xml 檔案。 例如，這些檔案可能儲存至您從 AD RMS 伺服器移至連線網際網路之工作站的 USB 隨身碟。

> [!NOTE]
> 不論您儲存這些檔案的方法為何，由於這些資料含有私密金鑰，因此請使用最佳的安全措施來加以保護。

##### 軟體保護的金鑰移轉至軟體保護的金鑰
使用此程序將 AD RMS 組態匯入至 Azure RMS，以產生由 Microsoft 所管理的 Azure RMS 租用戶金鑰。

###### 將組態資料匯入至 Azure RMS

1.  在連線網際網路的工作站上，下載並安裝 Azure RMS 的 Windows PowerShell 模組 (最低 2.1.0.0 版)，其中包括 [Import-AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx) Cmdlet。

    > [!TIP]
    > 如果您先前已下載及安裝此模組，請執行 `(Get-Module aadrm -ListAvailable).Version` 來檢查版本號碼

    如需安裝指示，請參閱[針對 Azure Rights Management 安裝 Windows PowerShell](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md)。

2.  使用 [**以系統管理員身分執行**] 選項啟動 Windows PowerShell，然後使用 [Connect-AadrmService](http://msdn.microsoft.com/library/azure/dn629415.aspx) Cmdlet 來連接 Azure RMS 服務：

    ```
    Connect-AadrmService
    ```
    出現提示時，輸入您的 [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] 租用戶系統管理員認證 (通常需要使用 Azure Active Directory 或 Office 365 的全域系統管理員帳戶)。

3.  使用 [Import-AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx) Cmdlet 上載第一個匯出的信任發行網域 (.xml) 檔案： 如果您因為擁有多個信任的發佈網域，而使得所擁有的 .xml 檔案不只一個，則您所選擇的檔案應包含已匯出的信任發佈網域，移轉之後您才能在 Azure RMS 使用該網域來保護內容。 使用下列命令：

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword -Active $True -Verbose
    ```
    例如：**Import-AadrmTpd -TpdFile E:\contosokey1.xml -ProtectionPassword -Active $true -Verbose**

    系統提示時，請輸入您稍早指定的密碼，並確認您想要執行此動作。

4.  當命令完成時，針對匯出信任發行網域而建立的每個 .xml 檔案重複步驟 3。 但對於這些檔案，請在執行匯入命令時，將 **-Active** 設為 **false**。 例如：**Import-AadrmTpd -TpdFile E:\contosokey2.xml -ProtectionPassword -Active $false -Verbose**

5.  使用 [Disconnect-AadrmService](http://msdn.microsoft.com/library/azure/dn629416.aspx) Cmdlet 來中斷 Azure RMS 服務的連線：

    ```
    Disconnect-AadrmService
    ```

您現在可以開始移至[Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration)。

##### HSM 保護的金鑰移轉至 HSM 保護的金鑰
它是兩部分的程序，可將 HSM 金鑰和 AD RMS 設定匯入至 Azure RMS，以產生由您管理 (BYOK) 的 Azure RMS 租用戶金鑰。

您必須先將 HSM 金鑰封裝，才能將其傳輸至 Azure RMS，然後再與設定資料一併匯入。

###### 第 1 篇：封裝 HSM 金鑰使其能傳輸至 Azure RMS

1.  遵循[規劃及實作 Azure Rights Management 租用戶金鑰](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md)主題中＜[實作整合您自己的金鑰 (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK)＞一節的步驟，並使用**產生並傳輸您的租用戶金鑰 - 透過網際網路**程序，但有下列例外：

    -   請勿遵循**產生您的租用戶金鑰**步驟，因為您已經從 AD RMS 部署取得對等項目。 您必須從 Thales 安裝中找出 AD RMS 伺服器所使用的金鑰，並在移轉期間使用這個金鑰。 Thales 加密金鑰檔案在本機伺服器上的命名通常是 **key_(keyAppName)_(keyIdentifier)**。

    -   請勿遵循**將租用戶金鑰傳輸至 Azure RMS**步驟，該步驟使用 Add-Aadrmkey 命令。  而是要使用 Import-AadrmTpd 命令，在上傳匯出的信任發行網域時，傳輸您備妥的 HSM 金鑰。

2.  在已連線到網際網路的工作站上，在 Windows PowerShell 工作階段中重新連線至 Azure RMS 服務。

現在您已備妥用於 Azure RMS 的 HSM 金鑰，您可以開始匯入您的 HSM 金鑰檔案與 AD RMS 設定資料。

###### 第 2 篇：將 HSM 金鑰和設定資訊匯入 Azure RMS

1.  請同樣在連線網際網路的工作站上、Windows PowerShell 工作階段中，上傳第一個匯出的信任發佈網域 (.xml) 檔案： 如果您因為擁有多個信任的發佈網域，而使得所擁有的 .xml 檔案不只一個，則您所選擇的檔案除了應包含已匯出的信任發佈網域外，該網域更應對應至您在轉移後要用來在 Azure RMS 保護內容的 HSM 金鑰。 使用下列命令：

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword -HsmKeyFile <PathToBYOKPackage> -Active $True -Verbose
    ```
    例如：**Import -TpdFile E:\no_key_tpd_contosokey1.xml  -HsmKeyFile E:\KeyTransferPackage-contosokey.byok -ProtectionPassword -Active $true -Verbose**

    系統提示時，請輸入您稍早指定的密碼，並確認您想要執行此動作。

2.  當命令完成時，針對匯出信任發行網域而建立的每個 .xml 檔案重複步驟 1。 但對於這些檔案，請在執行匯入命令時，將 **-Active** 設為 **false**。  例如：**Import -TpdFile E:\contosokey2.xml -HsmKeyFile E:\KeyTransferPackage-contosokey.byok -ProtectionPassword -Active $false -Verbose**

3.  使用 [Disconnect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) Cmdlet 來中斷 Azure RMS 服務的連線：

    ```
    Disconnect-AadrmService
    ```

您現在可以開始移至[Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration)。

##### 軟體保護的金鑰移轉至 HSM 保護的金鑰
它是三部分的程序，可將 AD RMS 組態匯入至 Azure RMS，以產生由您管理 (BYOK) 的 Azure RMS 租用戶金鑰。

您必須先從組態資料中擷取伺服器授權人憑證 (SLC) 金鑰，並將金鑰傳輸至內部部署 Thales HSM，再將 HSM 金鑰封裝並傳輸至 Azure RMS，然後匯入組態資料。

###### 第 1 篇：從組態資料中擷取 SLC，並將金鑰匯入至內部部署 HSM

1.  使用＜[規劃及實作 Azure Rights Management 租用戶金鑰](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md)＞主題的＜[實作整合您自己的金鑰 (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK)＞一節中的下列步驟：

    -   **產生並傳輸您的租用戶金鑰 – 透過網際網路**：**準備連線網際網路的工作站**

    -   **產生並傳輸您的租用戶金鑰 – 透過網際網路**：**準備中斷連線的工作站**

    請不要遵循這些步驟來產生租用戶金鑰，因為您在匯出的組態資料 (.xml) 檔案中已經有對等項目。 相反地，您將執行命令，從檔案中擷取這個金鑰，並將它匯入至內部部署 HSM。

2.  在中斷連線的工作站上，執行下列命令：

    ```
    KeyTransferRemote.exe -ImportRmsCentrallyManagedKey -TpdFilePath <TPD> -ProtectionPassword -KeyIdentifier <KeyID> -ExchangeKeyPackage <BYOK-KEK-pka-Region> -NewSecurityWorldPackage <BYOK-SecurityWorld-pkg-Region>
    ```
    例如，若為北美洲：**KeyTransferRemote.exe -ImportRmsCentrallyManagedKey -TpdFilePath E:\contosokey1.xml -ProtectionPassword -KeyIdentifier contosorms1key –- -ExchangeKeyPackage &lt;BYOK-KEK-pka-NA-1&gt; -NewSecurityWorldPackage &lt;BYOK-SecurityWorld-pkg-NA-1&gt;**

    其他資訊：

    -   ImportRmsCentrallyManagedKey 參數會指出作業是匯入 SLC 金鑰。

    -   如果您未在命令中指定密碼，則系統會提示您指定它。

    -   KeyIdentifier 參數是做為建立金鑰檔名稱的金鑰易記名稱。 您只能使用小寫的 ASCII 字元。

    -   ExchangeKeyPackage 參數會指定名稱開頭為 BYOK-KEK-pkg- 的區域特定金鑰交換金鑰 (KEK) 封裝。

    -   NewSecurityWorldPackage 參數會指定名稱開頭為 BYOK-SecurityWorld-pkg- 的安全性世界封裝。

    此命令會產生下列項目：

    -   An HSM 金鑰檔：%NFAST_KMDATA%\local\key_mscapi_&lt;KeyID&gt;

    -   已移除 SLC 的 RMS 組態資料檔：%NFAST_KMDATA%\local\no_key_tpd_ &lt; KeyID &gt;.xml

3.  如果您有多個 RMS 組態資料檔，請針對這些檔案的其餘檔案重複步驟 2。

現在已擷取您的 SLC，因此它是 HSM 金鑰，而您已準備好將它封裝並傳輸至 Azure RMS。

###### 第 2 篇：將 HSM 金鑰封裝並傳輸至 Azure RMS

1.  使用＜[規劃及實作 Azure Rights Management 租用戶金鑰](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md)＞主題的＜[實作整合您自己的金鑰 (BYOK)](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_ImplementBYOK)＞一節中的下列步驟：

    -   **產生並傳輸您的租用戶金鑰 – 透過網際網路**：**準備您的租用戶金鑰進行傳輸**

    -   **產生並傳輸您的租用戶金鑰 – 透過網際網路**：**將租用戶金鑰傳輸至 Azure RMS**

現在您已將 HSM 金鑰傳輸至 Azure RMS，可以匯入 AD RMS 組態資料 (僅包含新傳輸之租用戶金鑰的指標)。

###### 第 3 篇：將組態資料匯入至 Azure RMS

1.  請同樣在連線網際網路的工作站上、Windows PowerShell 工作階段中，複製已移除 SLC 的 RMS 組態檔 (從中斷連線的工作站中，%NFAST_KMDATA%\local\no_key_tpd_&lt;KeyID&gt;.xml)

2.  上傳第一個檔案。 如果您因為擁有多個信任的發佈網域，而使得所擁有的 .xml 檔案不只一個，則您所選擇的檔案除了應包含已匯出的信任發佈網域外，該網域更應對應至您在轉移後要用來在 Azure RMS 保護內容的 HSM 金鑰。 使用下列命令：

    ```
    Import-AadrmTpd -TpdFile <PathToNoKeyTpdPackageFile> -ProtectionPassword -HsmKeyFile <PathToKeyTransferPackage> -Active $true -Verbose
    ```
    例如：**Import -TpdFile E:\no_key_tpd_contosorms1key.xml -ProtectionPassword -HsmKeyFile E:\KeyTransferPackage-contosorms1key.byok -Active $true -Verbose**

    系統提示時，請輸入您稍早指定的密碼，並確認您想要執行此動作。

3.  當命令完成時，針對匯出信任發行網域而建立的每個 .xml 檔案重複步驟 2。 但對於這些檔案，請在執行匯入命令時，將 **-Active** 設為 **false**。 例如：**Import -TpdFile E:\no_key_tpd_contosorms2key.xml -ProtectionPassword -HsmKeyFile E:\KeyTransferPackage-contosorms1key.byok -Active $false -Verbose**

4.  使用 [Disconnect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) Cmdlet 來中斷 Azure RMS 服務的連線：

    ```
    Disconnect-AadrmService
    ```

您現在可以開始移至[Step 3. Activate your RMS tenant](../Topic/Migrating_from_AD_RMS_to_Azure_Rights_Management.md#BKMK_Step3Migration)。

### <a name="BKMK_Step3Migration"></a>步驟 3： 啟動您的 RMS 租用戶
＜[啟用 Azure Rights Management](../Topic/Activating_Azure_Rights_Management.md)＞主題會完整涵蓋這個步驟的指示。

> [!TIP]
> 如果您有 Office 365 訂閱，則可以從 Office 365 系統管理中心或 Azure 傳統入口網站中啟動 Azure RMS。 建議您使用 Azure 傳統入口網站，因為您將使用此管理入口網站來完成下一個步驟。

**如果已啟用 Azure RMS 租用戶，怎麼辦?**如果已對貴組織啟動 Azure RMS 服務，則使用者可能已經使用 Azure RMS，利用自動產生的租用戶金鑰 (和預設範本) 來保護內容，而不是 AD RMS 提供的現有金鑰 (和範本)。 不太可能在您的內部網路上妥善管理的電腦上發生此情況，因為會對您的 AD RMS 基礎結構自動設定它們。 但是，還是有可能發生在工作群組電腦或不常連接至內部網路的電腦上。 不幸的是，也很難找到這些電腦，就是這個原因，我們建議您不要在從 AD RMS 匯入組態資料之前啟動這些服務。

如果已啟動 Azure RMS 租用戶，而且可以識別這些電腦，請確定您在這些電腦上執行 CleanUpRMS_RUN_Elevated.cmd 指令碼，如步驟 5 中所述。 執行這個指令碼會強制它們重新初始化使用者環境，使他們可以下載更新的租用戶金鑰和匯入的範本。

### <a name="BKMK_Step4Migration"></a>步驟 4： 設定匯入的範本
因為所匯入範本的預設狀態為 [**已封存**]，所以如果您想要使用者能夠搭配使用這些範本與 Azure RMS，則必須將此狀態變更為 [**已發佈**]。

此外，如果 AD RMS 中的範本使用 **ANYONE** 群組，此群組會在您將範本匯入到 Azure RMS 時自動刪除；您必須將對等的群組或使用者和相同的權限，手動新增到已匯入的範本。 Azure RMS 的對等群組名為 **AllStaff-&lt;tenant_GUID&gt;@&lt;tenant_name&gt;.onmicrosoft.com**。 例如，Contoso 的這個群組可能看起來如下所示：**AllStaff-9c11c87a-ac8b-46a3-8d5c-f4d0b72ee29a@contoso.onmicrosoft.com**。

如果不確定您的 AD RMS 範本是否包括 ANYONE 群組，請展開[PowerShell script to identify AD RMS templates that include the ANYONE group](#BKMK_ScriptForANYONE)一節，在此步驟中複製和使用範例 PowerShell 指令碼來識別這些範本。 如需使用 Windows PowerShell with AD RMS 的詳細資訊，請參閱[使用 Windows PowerShell 來管理 AD RMS](https://technet.microsoft.com/library/ee221079%28v=ws.10%29.aspx)。

如果您在 Azure 傳統入口網站中複製其中一個預設權限原則範本，就可以看到您的組織自動建立的群組，然後在 [權限] 頁面上識別 [使用者名稱]。 不過，您無法使用 Azure 傳統入口網站將此群組新增至手動建立或匯入的範本，而必須改用下列其中一個 Azure RMS PowerShell 選項：

-   使用 [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx) PowerShell Cmdlet 將 "AllStaff" 群組和權限定義為權限定義物件，然後再次為其他各群組或使用者 (其已授予除了 ANYONE 群組以外原始範本中的權限) 執行此命令。 接著使用 [Add-AadrmTemplate](https://msdn.microsoft.com/en-us/library/azure/dn727076.aspx) Cmdlet 將所有這些權限定義物件新增至範本。

-   使用 [Export-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx) Cmdlet，將範本匯出到您可以編輯的 .XML 檔，以將 "AllStaff" 群組和權限新增到現有的群組和權限，然後使用 [Import-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx) Cmdlet 將此變更匯回到 Azure RMS 中。

> [!NOTE]
> 此 "AllStaff" 對等群組與 AD RMS 中的 ANYONE 組不完全相同："AllStaff" 群組包含您的 Azure 租用戶中的所有使用者，而 ANYONE 群組包含所有經過驗證的使用者 (有可能組織外部的使用者)。
> 
> 由於這兩個群組之間的差異，除了 "AllStaff" 群組以外，您可能還需要新增外部使用者。 目前不支援群組的外部電子郵件地址。

從 AD RMS 匯入之範本的外觀和行為就像您可以在 Azure 傳統入口網站中建立的自訂範本一樣。 若要將匯入的範本變更為已發佈，讓使用者可以看到它們並從應用程式中選取它們，或者對範本進行其他變更，請參閱[設定 Azure Rights Management 的自訂範本](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md)。

> [!TIP]
> 為了讓使用者在移轉程序期間具有更一致的經驗，除了這兩個變更以外，請不要對匯入的範本進行變更；並且不要發佈 Azure RMS 隨附的兩個預設範本，或在此時建立新的範本。 相反地，請等到完成移轉程序並解除委任 AD RMS 伺服器。

#### <a name="BKMK_ScriptForANYONE"></a>範例 Windows PowerShell 指令碼來識別包括 ANYONE 群組的 AD RMS 範本
本節包含範例指令碼，以協助您識別有 ANYONE 群組定義的 AD RMS 範本，如前一節所述。

*&#42;&#42;免責聲明：&#42;&#42;這個範例指令碼在任何 Microsoft 標準支援計劃或服務底下不受支援。 這個範例指令碼是依現狀提供，不含任何種類的擔保。*

```
import-module adrmsadmin New-PSDrive -Name MyRmsAdmin -PsProvider AdRmsAdmin -Root https://localhost -Force $ListofTemplates=dir MyRmsAdmin:\RightsPolicyTemplate foreach($Template in $ListofTemplates) { $templateID=$Template.id $rights = dir MyRmsAdmin:\RightsPolicyTemplate\$Templateid\userright $templateName=$Template.DefaultDisplayName if ($rights.usergroupname -eq "anyone") { $templateName = $Template.defaultdisplayname write-host "Template " -NoNewline write-host -NoNewline $templateName -ForegroundColor Red write-host " contains rights for " -NoNewline write-host ANYONE  -ForegroundColor Red } } Remove-PSDrive MyRmsAdmin -force
```

### <a name="BKMK_Step5Migration"></a>步驟 5： 重新設定用戶端使用 Azure RMS
對於 Windows 用戶端：

1.  [下載移轉指令碼](http://go.microsoft.com/fwlink/?LinkId=524619)：

    -   CleanUpRMS_RUN_Elevated.cmd

    -   Redirect_OnPrem.cmd

    這些指令碼會重設 Windows 電腦上的組態，使其使用 Azure RMS 服務，而不是 AD RMS。

2.  遵循重新導向指令碼 (Redirect_OnPrem.cmd) 中的指示來修改指令碼，以指向新的 Azure RMS 租用戶。

3.  在 Windows 電腦上，於使用者內容中以提高權限執行這些指令碼。

對於行動裝置用戶端和 Mac 電腦：

-   移除部署 [AD RMS 的行動裝置延伸模組](http://technet.microsoft.com/library/dn673574.aspx)時所建立的 DNS SRV 記錄。

#### 移轉指令碼所進行的變更
本節記載移轉指令碼所進行的變更。 此資訊僅供參考或進行疑難排解，或者，您可能會想要自己進行這些變更。

CleanUpRMS_RUN_Elevated.cmd：

-   刪除 %userprofile%\AppData\Local\Microsoft\DRM 和 %userprofile%\AppData\Local\Microsoft\MSIPC 資料夾的內容，包括任何子資料夾和任何具有長檔名的檔案。

-   刪除下列登錄機碼的內容：

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_LOCAL_MACHINE\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_CURRENT_USER\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation

    -   HKEY_LOCAL_MACHINE\SOFTWARE\WoW6432Node\Microsoft\MSIPC\ServiceLocation

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation

-   刪除下列登錄值：

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServerURL

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServer

Redirect_OnPrem.cmd：

-   針對下列每個位置中每個提供為參數的 URL，建立下列登錄值：

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\LicensingRedirection

    每個項目都有 **https://OldRMSserverURL/_wmcs/licensing** 的 REG_SZ 值，而其資料格式如下：**https://&lt;YourTenantURL&gt;/_wmcs/licensing**

    > [!NOTE]
    > *&lt;YourTenantURL&gt;* 具有下列格式：**{GUID}.rms.[Region].aadrm.com**。
    > 
    > 例如：5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com
    > 
    > 在針對 Azure RMS 執行 [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) Cmdlet 時，您可以藉由辨識 **RightsManagementServiceId** 值來找出該值。

### <a name="BKMK_Step6Migration"></a>步驟 6： 設定 Exchange Online 的 IRM 整合
如果先前已將 TPD 從 AD RMS 匯入至 Exchange Online，您必須移除此 TDP，才能在移轉至 Azure RMS 之後避免衝突的範本和原則。 若要這樣做，請使用 Exchange Online 中的 [Remove-RMSTrustedPublishingDomain](https://technet.microsoft.com/en-us/library/jj200720%28v=exchg.150%29.aspx) Cmdlet。

如果您選擇 **Microsoft 管理的** Azure RMS 租用戶金鑰拓撲：

-   請參閱[設定 Azure Rights Management 的應用程式](../Topic/Configuring_Applications_for_Azure_Rights_Management.md)主題中的[Exchange Online：IRM 設定](../Topic/Configuring_Applications_for_Azure_Rights_Management.md#BKMK_ExchangeOnline)一節。 本節包含一般執行的命令，可連接至 Exchange Online 服務、從 Azure RMS 匯入租用戶金鑰，以及啟用Exchange online 的 IRM 功能。 完成這些步驟之後，您將有完整的 RMS 功能與 Exchange Online 搭配。

如果您選擇**客戶管理的 (BYOK)** Azure RMS 租用戶金鑰拓撲：

-   您將有精簡的 RMS 功能與 Exchange Online 搭配，如＜[規劃及實作 Azure Rights Management 租用戶金鑰](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md)＞主題中的＜[BYOK 定價和限制](../Topic/Planning_and_Implementing_Your_Azure_Rights_Management_Tenant_Key.md#BKMK_Pricing)＞一節所述。

### <a name="BKMK_Step7Migration"></a>步驟 ７： 部署 RMS 連接器
如果您已經搭配使用 Exchange Server 或 SharePoint Server 的資訊版權管理 (IRM) 功能與 AD RMS，則必須先停用這些伺服器上的 IRM，並移除 AD RMS 組態。 然後，部署 Rights Management (RMS) 連接器，其可做為內部部署伺服器與 Azure RMS 之間的通訊介面 (轉送)。

最後，在這個步驟中，如果您已將用來保護電子郵件訊息的多個 TPD 匯入至 Azure RMS，則必須手動編輯 Exchange Server 電腦上的登錄，以將所有 TPD URL 重新導向至 RMS 連接器。

> [!NOTE]
> 開始之前，請查閱＜[Azure Rights Management 的需求](../Topic/Requirements_for_Azure_Rights_Management.md)＞主題的＜[支援 Azure RMS 的應用程式](../Topic/Requirements_for_Azure_Rights_Management.md#BKMK_SupportedApplications)＞一節的「支援 Azure RMS 的內部部署伺服器」，取得 RMS 連接器所支援的內部部署伺服器版本。

##### 停用 Exchange Server 上的 IRM 並移除 AD RMS 組態

1.  在每個 Exchange 伺服器上，找到下列資料夾並刪除該資料夾中的所有項目：\ProgramData\Microsoft\DRM\Server\S-1-5-18

2.  從其中一個 Exchange Server 中，使用 Exchange [Set_IRMConfiguration](http://technet.microsoft.com/library/dd979792.aspx) Cmdlet 先停用傳送給內部收件者之訊息的 IRM 功能：

    ```
    Set-IRMConfiguration -InternalLicensingEnabled $false
    ```

3.  然後，使用相同的 Cmdlet 停用傳送給外部收件者之訊息的 IRM 功能：

    ```
    Set-IRMConfiguration -ExternalLicensingEnabled $false
    ```

4.  接下來，使用相同的 Cmdlet 停用 Microsoft Office Outlook Web App 和 Microsoft Exchange ActiveSync 中的 IRM：

    ```
    Set-IRMConfiguration -ClientAccessServerEnabled $false
    ```

5.  最後，使用相同的 Cmdlet 清除任何快取的憑證：

    ```
    Set-IRMConfiguration -RefreshServerCertificates
    ```

6.  在每個 Exchange Server 上，現在請重設 IIS，例如，以系統管理員身分執行命令提示字元，並輸入 **iisreset**。

##### 停用 SharePoint Server 上的 IRM 並移除 AD RMS 組態

1.  確定未從 RMS 保護的文件庫中簽出文件。 如果有，則它們在這個程序結束時會變成無法存取。

2.  在 SharePoint 管理中心網站的 [**快速啟動**] 區段中，按一下 [**安全性**]。

3.  在 [**安全性**] 頁面的 [**資訊原則**] 區段中，按一下 [**設定資訊版權管理**]。

4.  在 [**資訊版權管理**] 頁面的 [**資訊版權管理**] 區段中，選取 [**不要在此伺服器使用 IRM**]，然後按一下 [**確定**]。

5.  在每個 SharePoint Server 電腦上，刪除 \ProgramData\Microsoft\MSIPC\Server\*&lt;執行 SharePoint Server 之帳戶的 SID&gt;* 資料夾的內容。

##### 安裝和設定 RMS 連接器

-   使用[部署 Azure Rights Management 連接器](../Topic/Deploying_the_Azure_Rights_Management_Connector.md)主題中的指示。

##### 對於僅 Exchange 和多個 TPD：編輯登錄

-   在每個 Exchange Server 上，針對匯入的每個額外 TPD 手動新增下列登錄機碼，以將 TPD URL 重新導向至 RMS 連接器。 這些登錄項目僅供移轉，而且不是由 Microsoft RMS 連接器的伺服器組態工具所新增。

    進行這些登錄編輯時，請使用下列指示：

    -   將 *ConnectorFQDN* 取代為您在 DNS 中為連接器所定義的名稱。 例如，**rmsconnector.contoso.com**。

    -   連接器 URL 使用 HTTP 或 HTTPS 前置碼，是取決於設定連接器使用 HTTP 還是 HTTPS 與內部部署伺服器進行通訊。

    **Exchange 2013：**

    |登錄路徑|類型|值|資料|
    |--------|------|-----|------|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection|Reg_SZ|https://&lt;AD RMS 內部網路授權 URL&gt;/_wmcs/licensing|下列其中一項，視您於 Exchange 伺服器至 RMS 連接器中使用 HTTP 或 HTTPS 而定：<br /><br />-   http://&lt;connectorFQDN&gt;/_wmcs/licensing<br />-   https://&lt;connectorName&gt;/_wmcs/licensing|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection|Reg_SZ|https://&lt;AD RMS 外部網路授權 URL&gt;/_wmcs/licensing|下列其中一項，視您於 Exchange 伺服器至 RMS 連接器中使用 HTTP 或 HTTPS 而定：<br /><br />-   http://&lt;connectorFQDN&gt;/_wmcs/licensing<br />-   https://&lt;connectorFQDN&gt;/_wmcs/licensing|
    **對於 Exchange Server 2010：**

    |登錄路徑|類型|值|資料|
    |--------|------|-----|------|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection|Reg_SZ|https://&lt;AD RMS 內部網路授權 URL&gt;/_wmcs/licensing|下列其中一項，視您於 Exchange 伺服器至 RMS 連接器中使用 HTTP 或 HTTPS 而定：<br /><br />-   http://&lt;connectorName&gt;/_wmcs/licensing<br />-   https://&lt;connectorName&gt;/_wmcs/licensing|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection|Reg_SZ|https://&lt;AD RMS 外部網路授權 URL&gt;/_wmcs/licensing|下列其中一項，視您於 Exchange 伺服器至 RMS 連接器中使用 HTTP 或 HTTPS 而定：<br /><br />-   http://&lt;connectorName&gt;/_wmcs/licensing<br />-   https://&lt;connectorName&gt;/_wmcs/licensing|

完成這些程序之後，請務必閱讀＜[部署 Azure Rights Management 連接器](../Topic/Deploying_the_Azure_Rights_Management_Connector.md)＞主題中的＜**後續步驟**＞一節。

### <a name="BKMK_Step8Migration"></a>步驟 8： 解除委任 AD RMS
選用：移除 Active Directory 中的服務連線點 (SCP)，以避免電腦探索內部部署 Rights Management 基礎結構。 這是選擇性的做法，取決於您在登錄中設定的重新導向 (如藉由執行移轉指令碼)。 若要移除服務連線點，請使用 [Rights Management Services 管理工具組](http://www.microsoft.com/download/details.aspx?id=1479)中的 AD SCP 註冊工具。

監視 AD RMS 伺服器中的活動，如藉由檢查[系統健康情況報告中的要求](https://technet.microsoft.com/library/ee221012%28v=ws.10%29.aspx)、[ServiceRequest 資料表](http://technet.microsoft.com/library/dd772686%28v=ws.10%29.aspx)或[使用者存取受保護內容的稽核](http://social.technet.microsoft.com/wiki/contents/articles/3440.ad-rms-frequently-asked-questions-faq.aspx)。 確認 RMS 用戶端不再與這些伺服器進行通訊而且用戶端順利使用 Azure RMS 時，您可以從這些伺服器中移除 AD RMS 伺服器角色。 如果您使用專用伺服器，則可能會想要進行警告性步驟，即先關閉伺服器一段時間，確定未報告任何可能需要重新啟動這些伺服器的問題，以確保在您調查用戶端未使用 Azure RMS 的原因時服務不中斷。

解除委任 AD RMS 伺服器之後，您可能會想要利用這個機會在 Azure 傳統入口網站中檢閱範本並將其合併，讓使用者擁有較少的選擇，或重新設定它們，甚至加入新的範本。 這可能也是發佈預設範本的好時機。 如需詳細資訊，請參閱[設定 Azure Rights Management 的自訂範本](../Topic/Configuring_Custom_Templates_for_Azure_Rights_Management.md)。

### <a name="BKMK_Step9Migration"></a>步驟 9： 重新設定 Azure RMS 租用戶金鑰
因為重新設定金鑰會建立使用 RMS 加密 2 的新租用戶金鑰，所以如果 AD RMS 部署使用 RMS 加密模式 1，則完成移轉時需要這個步驟。 只有在移轉程序期間才支援搭配使用 Azure RMS 與加密模式 1。

這是選擇性步驟，但在完成移轉時建議使用，即使您執行 RMS 加密模式 2 也是一樣，因為它可以協助保護 Azure RMS 租用戶金鑰，使其沒有 AD RMS 金鑰的潛在安全性漏洞。 重新設定 Azure RMS 租用戶金鑰 (也稱為「輪換金鑰」) 時，會建立新的金鑰，並封存原始金鑰。 不過，因為從某個金鑰移至另一個金鑰不會立即進行，而是需要幾週的時間，所以請不要等到懷疑原始金鑰有漏洞，而是完成移轉之後立即重新設定 RMS 租用戶金鑰。

重新設定 Azure RMS 租用戶金鑰：

-   如果您的 RMS 租用戶金鑰是由 Microsoft 所管理：連絡 Microsoft 客戶支援服務 (CSS) 並證明您是 RMS 租用戶系統管理員。

-   如果您的 RMS 租用戶金鑰是由您所管理 (BYOK)：重複 BYOK 程序，以透過網際網路或親自產生並建立新的金鑰。

如需管理 RMS 租用戶金鑰的詳細資訊，請參閱＜[Azure Rights Management 租用戶金鑰的作業](../Topic/Operations_for_Your_Azure_Rights_Management_Tenant_Key.md)＞。

## 請參閱
[設定 Azure Rights Management](../Topic/Configuring_Azure_Rights_Management.md)

