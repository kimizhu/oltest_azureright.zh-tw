---
description: na
keywords: na
title: Rights Management sharing application administrator guide
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d9992e30-f3d1-48d5-aedc-4e721f7d7c25
---
# Rights Management 共用應用程式系統管理員指南 (英文)
如果您負責企業網路上的 Microsoft Rights Management 共用應用程式，或是您想獲得比 [Rights Management 共用應用程式使用者指南 &#40;英文&#41;](../Topic/Rights_Management_sharing_application_user_guide.md)或 [適用於 Windows 的 Microsoft Rights Management 共用應用程式的常見問題集](http://go.microsoft.com/fwlink/?LinkId=303971) 中更多技術資訊，請使用下列資訊：

-   [Microsoft Rights Management 共用應用程式的自動部署](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_ScriptedInstall)

    -   [確認安裝成功](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted)

    -   [解除安裝命令](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_uninstallscripted)

    -   [隱藏自動更新](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_SuppressAutomaticUpdates)

    -   [僅 Azure RMS：設定文件追蹤](#BKMK_DocumentTracking)

    -   [僅限 AD RMS：支援貴組織內有多個電子郵件網域](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_FederatedDomains)

-   [Microsoft Rights Management 共用應用程式技術概觀](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_AdminOverview)

    -   [保護的層級 – 原生和一般](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_LevelsofProtection)

    -   [支援的檔案類型與副檔名](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_SupportFileTypes)

    -   [變更檔案的預設保護層級](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_ChangeDefaultProtection)

> [!TIP]
> 如果您是 RMS 共用應用程式的新手，或想知道更多資訊，請參閱 [RMS 如何保護所有檔案類型 – 使用 RMS 共用應用程式](https://curah.microsoft.com/191031/how-rms-protects-all-file-types-by-using-the-rms-sharing-app)。

RMS 共用應用程式最適合與 Azure RMS 搭配使用，因為此部署設定支援傳送受保護的附件給組織中另一個使用者，並支援電子郵件通知和文件追蹤與撤銷等選項。  不過，遵守一些限制，它也可搭配內部部署版本 AD RMS。 如需 Azure RMS 和 AD RMS 支援的功能完整比較，請參閱[比較 Azure Rights Management 與 AD RMS](https://technet.microsoft.com/library/jj739831.aspx)。 如果您有 AD RMS 並想要移轉至 Azure RMS，請參閱[從 AD RMS 移轉至 Azure Rights Management](https://technet.microsoft.com/library/dn858447.aspx)。

## <a name="BKMK_ScriptedInstall"></a>Microsoft Rights Management 共用應用程式的自動部署
RMS 共用應用程式的 Windows 版本支援指令碼式安裝，這使得它非常適合用於企業部署。

此安裝的唯一必要條件是電腦執行 Windows 7 Service Pack 1 以上的版本且已安裝 Microsoft Framework 4.0 以上的版本。 如果您需要安裝 Microsoft.NET Framework 4.0，可以[從 Microsoft 下載中心下載並安裝](http://www.microsoft.com/download/details.aspx?id=17718)。

#### 若要下載 RMS 共用應用程式以進行自動部署

1.  請移至 Microsoft 下載中心的[適用於 Windows 的 Microsoft Rights Management 共用應用程式](http://www.microsoft.com/download/details.aspx?id=40857)頁面，按一下 [下載]。

2.  選取並下載您需要的檔案。 有兩個用戶端安裝套件：一個用於 Windows 64 位元 (Microsoft Rights Management 共用應用程式 x64.zip)，和另一個用於 Windows 32 位元 (Microsoft Rights Management 共用應用程式 x86.zip)。

3.  從壓縮的安裝套件將檔案解壓縮，例如按兩下套件。 然後將解壓縮的檔案複製到用戶端電腦可以存取的網路位置。

RMS 共用應用程式的安裝程式套件支援不同的部署案例，並包括下列項目：

|說明|部署狀況|
|------|--------|
|Microsoft 線上登入小幫手|下列項目的必要條件：<br /><br />-   Office 2010 和 Azure RMS<br />-   Office 2013 和 Azure RMS，如果您尚未安裝 [2015 年 6 月9 日，Office 2013 的更新](https://support.microsoft.com/kb/3054853) (KB3054853)|
|Hotfix for Office (KB2596501)|下列項目的必要條件：<br /><br />-   Office 2010 和 Azure RMS<br />-   Office 2010 和 Active Directory RMS|
|讓 AD RMS Client 1.0 可與 Azure RMS 搭配使用的 Hotfix (KB2843630)|下列項目的必要條件：<br /><br />-   Office 2010 和 Azure RMS<br />-   Office 2010 和 Active Directory RMS|
|AD RMS Client 和 RMS 共用應用程式|下列項目的必要條件：<br /><br />-   Office 2016 或 Office 2013 和 Azure RMS 或 Active Directory RMS<br />-   Office 2010 和 Azure RMS<br />-   Office 2010 和 Active Directory RMS<br />-   僅 RMS 共用應用程式和 Office 增益集|
|功能區的 Office 增益集|下列項目的必要條件：<br /><br />-   Office 2016 或 Office 2013 和 Azure RMS 或 Active Directory RMS<br />-   Office 2010 和 Azure RMS<br />-   Office 2010 和 Active Directory RMS<br />-   僅 RMS 共用應用程式和 Office 增益集|
|Azure Active Directory Rights Management 準備工具|下列項目的必要條件：<br /><br />-   Office 2010 和 Azure RMS|
使用下列程序來識別為這些部署案例部署 RMS 共用應用程式所需的命令：

-   **Office 2016 或 Office 2013 和 Azure RMS 或 Active Directory RMS**

    您的使用者執行 Office 2016 或 Office 2013，您的組織使用 Azure RMS 或 Active Directory RMS，且使用者與使用 Azure RMS 或 Active Directory RMS 的其他組織共同作業。

-   **Office 2010 和 Azure RMS**

    您的使用者執行 Office 2010，您的組織使用 Azure RMS，且使用者與使用 Azure RMS 或 Active Directory RMS 的其他組織共同作業。

-   **Office 2010 和 Active Directory RMS**

    您的使用者執行 Office 2010，您的組織使用 AD RMS，且使用者與使用 Azure RMS 的其他組織共同作業。

-   **僅 RMS 共用應用程式和 Office 增益集**

    您的使用者執行 Office 2016、Office 2013 或 Office 2010，您的組織使用 AD RMS，且使用者不需與使用 Azure RMS 的其他組織共同作業。 此安裝可讓您只安裝共用應用程式和 Office 增益集。

> [!NOTE]
> 在這些案例中，如果您的組織執行 AD RMS，則您的使用者可以接收來自其他使用 Azure RMS 之組織的受保護內容，但您的使用者無法將受保護內容傳送給使用 Azure RMS 之組織中的使用者。 不過，如果您的組織執行 Azure RMS，您的使用者可以傳送和接收來自其他組織的受保護內容。

您必須重新啟動電腦，才能完成每個程序的安裝。 您可以使用命令 (例如 shutdown /i) 起始自動重新啟動。

#### 若要為 Office 2016 或 Office 2013 和 Azure RMS 或 Active Directory RMS 部署 RMS 共用應用程式

-   在您想要安裝 RMS 共用應用程式和相關元件的每一部電腦上，以提高的權限執行下列命令：

    ```
    setup.exe /s
    ```

若要確認是否成功，請參閱本主題中的＜[確認安裝成功](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted)＞一節。

#### 若要為 Office 2010 和 Azure RMS 部署 RMS 共用應用程式

1.  您必須是 Office 365 或 Azure Active Directory 租用戶的全域管理員，才可以藉由執行 Azure Active Directory Rights Management 準備工具取得貴組織的憑證服務 URL。 您只需要在單一電腦上執行此工具一次。 當您在每一部電腦上安裝 RMS 共用應用程式時，將使用憑證服務 URL：

    1.  使用本機系統管理員帳戶登入電腦。

    2.  在該電腦上[下載並安裝 Microsoft Online 登入小幫手](http://www.microsoft.com/download/details.aspx?id=28177)。

    3.  執行下列命令以查看顯示在螢幕上的憑證服務 URL，您可加以複製儲存供下個步驟使用：

        -   Windows 8.1 和 Windows 8，64 位元：

            ```
            x64\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        -   Windows 8.1 和 Windows 8，32 位元：

            ```
            X86\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        -   Windows 7，64 位元：

            ```
            x64\win7\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        > [!NOTE]
        > 此命令可能會提示您輸入 Azure 認證。 如果電腦未加入網域，系統會提示您。 如果電腦已加入網域，此工具可能可以使用快取的認證。

2.  在您要安裝 RMS 共用應用程式的每一部電腦上，以提高的權限執行下列命令：

    ```
    setup.exe /s /configureO2010Admin /certificationUrl <certification_url>
    ```

3.  在您要安裝 RMS 共用應用程式的每一部電腦上，使用者必須執行下列命令 (不需使用提高的權限)。 有不同的方式可達到這個目的，包括要求使用者執行命令 (例如，電子郵件中的連結或技術支援入口網站上的連結)，或您可以將它加入使用者的登入指令碼：

    ```
    bin\RMSSetup.exe /configureO2010Only
    ```

若要確認是否成功，請參閱本主題中的＜[確認安裝成功](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted)＞一節。

#### 若要為 Office 2010 和 Active Directory RMS 部署 RMS 共用應用程式

1.  在您要安裝 RMS 共用應用程式的每一部電腦上，以提高的權限執行下列命令：

    ```
    setup.exe /s /configureO2010Admin
    ```

2.  在您要安裝 RMS 共用應用程式的每一部電腦上，使用者必須執行下列命令 (不需使用提高的權限)。 有不同的方式可達到這個目的，包括要求使用者執行命令 (例如，電子郵件中的連結或技術支援入口網站上的連結)，或您可以將它加入使用者的登入指令碼：

    -   Windows 10、Windows 8.1、Windows 8，64 位元：

        ```
        x64\aadrmprep.exe /configureO2010
        ```

    -   Windows 10、Windows 8.1、Windows 8，32 位元：

        ```
        X86\aadrmprep.exe /configureO2010
        ```

    -   Windows 7，64 位元：

        ```
        x64\win7\aadrmpep.exe /configureO2010
        ```

若要確認是否成功，請參閱本主題中的＜[確認安裝成功](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted)＞一節。

#### 若僅安裝 RMS 共用應用程式和 Office 增益集

1.  使用下列命令安裝 AD RMS Client 和 RMS 共用應用程式：

    -   64 位元 Windows：

        ```
        x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    -   32 位元 Windows：

        ```
        X86\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    例如：`\\server5\apps\rms\x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "C:\Log files\ipviewerinstall.log"`

2.  使用下列命令安裝 Office 增益集：

    -   64 位元版本的 Office：

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "<log file path and name>"
        ```

    -   32 位元版本的 Office：

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x86\Setup.msi" /L*v "<log file path and name>"
        ```

    例如：`\\server5\apps\rms\msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "C:\Log files\rmsofficeinstall.log"`

若要確認是否成功，請參閱本主題中的＜[確認安裝成功](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_verifyscripted)＞一節。

### <a name="BKMK_verifyscripted"></a>確認安裝成功
您可以使用安裝記錄檔來確認安裝成功。

##### 若要確認 Office 2016 或 Office 2013 和 Azure RMS 或 Active Directory RMS 的 RMS 共用應用程式安裝成功

-   若要確認在每部電腦上 Setup.exe 命令執行成功，請在 *%temp%\RMS_installer_&lt;guid&gt;* 資料夾中搜尋安裝記錄檔 **RMInstaller.log**，然後找到結束代碼。

    成功安裝的結束代碼是 0，任何其他數字都表示安裝失敗。

    範例記錄檔名稱：**C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0\RMInstaller.log**

##### 若要確認 Office 2010 和 Azure RMS 的 RMS 共用應用程式安裝成功

1.  若要確認在每部電腦上 Setup.exe 命令執行成功，請在 *%temp%\RMS_installer_&lt;guid&gt;* 資料夾中搜尋安裝記錄檔 **RMInstaller.log**，然後找到結束代碼。

    成功安裝的結束代碼是 0，任何其他數字都表示安裝失敗。

    範例記錄檔名稱：**C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0**

2.  若要確認 RMSSetup.exe 命令執行成功，使用者的 *%localappdata%\microsoft\drm* 資料夾中應已建立下列檔案：

    -   CERT-Machine-2048.drm

    -   CERT-Machine.drm

    -   CLC-&#42;.drm

    -   GIC-&#42;.drm

    CLC-&#42;.drm 檔案的範例：

    **CLC-alice@isvtenant999.onmicrosoft.com-{1b9cfccf;k5b11;k4a10;kac15;k29b2b6980f4c}.drm**

##### 若要確認 Office 2010 和 Active Directory RMS 的 RMS 共用應用程式安裝成功

1.  若要確認在每部電腦上 Setup.exe 命令執行成功，請在 *%temp%\RMS_installer_&lt;guid&gt;* 資料夾中搜尋安裝記錄檔，然後找到結束代碼。

    成功安裝的結束代碼是 0，任何其他數字都表示安裝失敗。

    範例記錄檔名稱：**C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0**

2.  若要確認在每部電腦上 aadrmprep.exe 命令執行成功，請在安裝記錄檔中搜尋下列文字：**aadrmprep.exe exited with status SUCCESS**

    > [!NOTE]
    > 有時候，這項安裝可能執行兩次；第一次出現失敗，第二次成功。

    如果您想要手動檢查這項工具所產生的登錄變更，登錄變更如下：

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\Federation]

        "FederationHomeRealm"="urn:HostedRmsOnlineService:Certification"

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\Federation]

        "FederationHomeRealm"="urn:HostedRmsOnlineService:Certification"

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\Activation]

        @="&lt;certification url&gt;"

    -   [HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\14.0\Common\DRM]

        DefaultUser="&lt;default_user&gt;"

##### 若要確認僅 RMS 共用應用程式和 Office 增益集的安裝成功

1.  若要確認 Setup_ipviewer.exe 命令執行成功，請在安裝記錄檔中搜尋下列文字：**Installation success or error status:0**

    安裝成功的記錄範例

    **MSI (s) (F0:B8) [14:19:57:854]:Product:Active Directory Rights Management Services Client 2.1 -- Installation completed successfully.**

    **MSI (s) (F0:B8) [14:19:57:854]:Windows Installer installed the product. Product Name:Active Directory Rights Management Services Client 2.1. Product Version:1.0.1179.1. Product Language:1033. 製造商：Microsoft Corporation. 安裝成功或錯誤狀態：0.**

2.  若要確認在每部電腦上 Office 增益集安裝成功，請在安裝記錄檔中搜尋下列文字：**Installation success or error status:0**

    安裝成功的記錄範例

    **MSI (s) (9C:88) [18:49:04:007]:Product:Microsoft RMS Office Addins -- Installation completed successfully.**

    **MSI (s) (9C:88) [18:49:04:007]:Windows Installer installed the product. Product Name:Microsoft RMS Office Addins. Product Version:1.0.7. Product Language:1033. 製造商：Microsoft. Installation success or error status:0.**

### <a name="BKMK_uninstallscripted"></a>解除安裝命令
這些部署所需的安裝命令並非全都支援解除安裝命令。 您可以解除安裝 AD RMS Client 和共用應用程式，也可以解除安裝 Office 增益集。 使用下列命令來解除安裝這些元件。

##### 若要解除安裝 AD RMS Client 和 RMS 共用應用程式

-   使用下列命令：

    -   64 位元 Windows：

        ```
        x64\setup_ipviewer.exe /uninstall /quiet
        ```

    -   32 位元 Windows：

        ```
        x86\setup_ipviewer.exe /uninstall /quiet
        ```

##### 若要解除安裝 Office 增益集

-   使用下列命令：

    -   64 位元版本的 Office：

        ```
        msiexec /x \x64\Setup[64].msi /quiet
        ```

    -   32 位元版本的 Office：

        ```
        msiexec /x \x86\Setup.msi /quiet
        ```

### <a name="BKMK_SuppressAutomaticUpdates"></a>隱藏自動更新
根據預設，如果有更新版本的 RMS 共用應用程式，系統會通知使用者，並提示您下載它。 您可以藉由編輯下列登錄隱藏此通知：

1.  瀏覽至 **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC**，如果不存在的話，請建立名為 **RmsSharingApp** 的新機碼。

2.  選取 **RmsSharingApp**，建立新的 DWORD 值 **AllowUpdatePrompt**，並將值設定為 **0**。

因為 WSUS 不支援 RMS 共用應用程式，您可以使用下列技巧來測試任何新版本的 RMS 共用應用程式，再將它部署至所有使用者：

1.  在所有使用者的電腦上，執行指令碼來隱藏自動更新。 在系統管理員用來測試新版本的電腦上，請勿執行此指令碼。

2.  當有新版本可用時，系統管理員會下載並進行測試。

3.  當測試完成並已解決任何問題，請使用本指南中的自動部署指示，將最新版本部署到所有使用者。

### <a name="BKMK_DocumentTracking"></a>僅 Azure RMS：設定文件追蹤
如果您有[支援文件追蹤的訂閱](https://technet.microsoft.com/en-us/dn858608)，您的組織預設會替所有使用者啟用文件追蹤網站。文件追蹤會顯示資訊，像是嘗試存取使用者共用之受保護文件的人的電子郵件地址、這些人何時嘗試存取它們、他們的位置等。如果基於隱私權需求您的組織禁止顯示這項資訊，您可以使用 [Disable-AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623032) Cmdlet 停用對文件追蹤網站的存取。您隨時可以使用 [Enable-AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623037) 重新啟用對網站的存取，且可以使用 [Get-AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623037) 檢查目前是啟用或停用存取。

 若要執行這些 Cmdlet，您至少必須有適用於 Windows PowerShell 的 Azure RMS 模組的最新版本 **2.3.0.0**。如需安裝指示，請參閱＜[安裝 Windows PowerShell for Azure Rights Management](https://technet.microsoft.com/library/jj585012.aspx)＞。

> [!TIP]
> 如果您先前已下載及安裝此模組，請執行以下 Cmdlet 檢查版本號碼：`(Get-Module aadrm –ListAvailable).Version`

必須允許下列用於文件追蹤的 URL (例如，若您使用增強安全性的 Internet Explorer，將其加入您的信任網站)：

-   https://&#42;.azurerms.com

-   https://ecn.dev.virtualearth.net

    > [!NOTE]
    > 此 URL 是 Bing 地圖。

-   https://&#42;.microsoftonline.com

-   https://&#42;.microsoftonline-p.com

### <a name="BKMK_FederatedDomains"></a>僅限 AD RMS：支援貴組織內有多個電子郵件網域
如果您使用 AD RMS，且貴組織中的使用者有多個電子郵件網域，或許是導因於合併或收購，您就必須進行下列登錄編輯：

1.  瀏覽至 **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC**，如果不存在的話，請建立名為 **RmsSharingApp** 的新機碼。

2.  選取 [RmsSharingApp]，建立新的名為 **FederatedDomains** 的多字串值，然後加入您的組織使用的所有網域和子網域。 不支援萬用字元。

    例如：Coho Vineyard &amp; Winery 公司有標準電子郵件網域 **cohovineyardandwinery.com**，但因為合併的關係，也使用電子郵件網域 **cohowinery.com**、**eastcoast.cohowinery.com** 和 **cohovineyard**。 系統管理員在 [FederatedDomains] 值資料輸入：**cohowinery.com; eastcoast.cohowinery.com; cohovineyard**

如果您不做此登錄變更，使用者可能無法使用受到組織中其他使用者保護的內容。 如果您使用 Azure RMS，就不需要進行此登錄編輯。

## <a name="BKMK_AdminOverview"></a>Microsoft Rights Management 共用應用程式技術概觀
Microsoft Rights Management 共用應用程式是可選擇性下載的應用程式，適用於 Microsoft Windows 和其他提供下列功能的平台：

-   保護單一檔案、大量保護多個檔案、以及保護選取之資料夾內的所有檔案。

-   完整支援對所有類型檔案的保護，以及對常用文字和影像檔案類型的內建檢視器。

-   對不支援 RMS 保護的檔案提供一般保護。

-   與使用 Office 資訊版權管理 (IRM) 保護的檔案之間有完全互通性。

-   與使用 SharePoint、FCI 和支援的 PDF 撰寫工具保護的 PDF 檔案之間有完全互通性。

Microsoft Rights Management共用應用程式使用新的 [AD RMS Client 2.1 執行階段](http://www.microsoft.com/download/details.aspx?id=38396)。 使用 AD RMS 2.1 的功能，Microsoft Rights Management 共用應用程式的功能可提供一般使用者簡單的保護和使用體驗。

使用 2013 年 10 月版本的 RMS，使用 Office 2010 就可以原生保護文件，然後將它們傳送給另一家公司的人，他們再使用 Azure RMS 取用文件。 除此之外，使用此版本，如果您使用「密碼編譯模式 2」的 AD RMS，您可以使用個人版 RMS，以及向使用 Azure RMS 的其他公司中的人取用內容。 如需密碼編譯模式 2 的詳細資訊，請參閱＜[AD RMS 密碼編譯模式](http://technet.microsoft.com/library/hh867439%28v=ws.10%29.aspx)＞。

### <a name="BKMK_LevelsofProtection"></a>保護的層級 – 原生和一般
Microsoft Rights Management 共用應用程式支援兩個不同的層級的保護，如下表所述。

|保護類型|原生|泛型|
|--------|------|------|
|說明|針對文字、影像、Microsoft Office (Word、Excel、PowerPoint) 檔案、.pdf 檔案及其他支援 Azure RMS 的應用程式檔案類型，原生保護提供了包含加密和增強權利 (權限) 的強力層級保護。|針對所有其他應用程式和檔案類型，一般保護提供包含檔案封裝 (使用 .pfile 檔案類型) 和驗證 (確認使用者是否獲得開啟檔案授權) 的保護層級。|
|保護|完整加密檔案並以下列方式強制執行保護：<br /><br />-   受保護的內容轉譯之前，透過電子郵件收到檔案或是透過檔案或共用權限存取檔案的人，必須成功通過驗證。<br />-   此外，當檔案受到保護時，若要在 IP 檢視器中 (適用於受保護的文字和影像檔) 或相關聯的應用程式中 (適用於所有其他支援的檔案類型) 轉譯內容時，將完全強制執行內容擁有者所設定的使用權限與原則。|以下列方式強制執行檔案保護：<br /><br />-   受保護的內容轉譯之前，獲得開啟檔案授權和獲得檔案存取權的人，必須成功通過驗證。 如果授權失敗，檔案不會開啟。<br />-   系統會顯示內容擁有者所設定的使用權限與原則，以通知授權使用者其預定使用原則。<br />-   不過，稽核授權的使用者開啟並存取檔案的記錄時，非支援應用程式不會強制執行使用權限。|
|預設檔案類型|這是下列檔案類型的預設保護層級：<br /><br />-   文字和影像檔案<br />-   Microsoft Office (Word, Excel, PowerPoint) 檔案<br />-   可攜式文件格式 (.pdf)<br /><br />如需詳細資訊，請參閱下節：[支援的檔案類型與副檔名](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_SupportFileTypes)。|這是完整保護不支援的所有其他檔案類型 (如.vsdx, .rtf 等等) 的預設保護。|
您可以變更 RMS 共用應用程式套用的預設保護層級。 您可以將預設的原生層級變更為一般、從一般變更為原生，甚至阻止 RMS 共用應用程式套用保護。 如需詳細資訊，請參閱本主題中的[變更檔案的預設保護層級](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_ChangeDefaultProtection)一節。

### <a name="BKMK_SupportFileTypes"></a>支援的檔案類型與副檔名
下表列出 Microsoft Rights Management 共用應用程式原生支援的檔案類型。 當套用原生保護時，這些類型檔案的原始副檔名會變更，且這些檔案會變成唯讀。

此外，當 RMS 共用應用程式原生保護使用者藉由共用保護的 Word、Excel 或 PowerPoint 檔案，這個動作會自動建立第二個檔案，它是原始檔案的副本，具有相同的檔名，但副檔名為 **.ppdf**¹。 這個版本的檔案可確保安裝了 RMS 共用應用程式的收件者可以隨時開啟已套用原生保護的檔案。

受到一般保護的檔案，原始檔案的副檔名一律會變更為 .pfile。

> [!WARNING]
> 如果您有防火牆、Web proxy 或會檢查並根據副檔名採取動作的安全性軟體，您可能需要重新設定這些安全性功能以支援這些新的副檔名。

|原始副檔名|受 RMS 保護的副檔名|
|---------|----------------|
|.txt|.ptxt|
|.xml|.pxml|
|.jpg|.pjpg|
|.jpeg|.ppng|
|.pdf|.ppdf|
|.png|.ppng|
|.tiff|.ptiff|
|.bmp|.pbmp|
|.gif|.pgif|
|.giff|.pgiff|
|.jpe|.pjpe|
|.jfif|.pjfif|
|.jif|.pjif|
|.jt|.pjt|
¹ PDF 轉譯由 Foxit 提供。 Copyright © 2003–2014 by Foxit Corporation.

下表列出 Microsoft Rights Management 共用應用程式在 Microsoft Office 2016、Office 2013 和 Office 2010 中原生支援的檔案類型。 這些檔案受 RMS 保護後副檔名維持不變。

|Office 支援的檔案類型|Office 支援的檔案類型|
|------------------|------------------|
|.doc<br /><br />.docm<br /><br />.docx<br /><br />.dot<br /><br />.dotm<br /><br />.dotx<br /><br />.potm<br /><br />.potx<br /><br />.pps<br /><br />.ppsm<br /><br />.ppsx<br /><br />.ppt<br /><br />.pptm|.pptx<br /><br />.thmx<br /><br />.xla<br /><br />.xlam<br /><br />.xls<br /><br />.xlsb<br /><br />.xlt<br /><br />.xlsm<br /><br />.xlsx<br /><br />.xltm<br /><br />.xltx<br /><br />.xps|

### <a name="BKMK_ChangeDefaultProtection"></a>變更檔案的預設保護層級
您可以編輯登錄來變更 RMS 共用應用程式對檔案的保護。 例如，您可以強制支援原生保護的檔案受到 RMS 共用應用程式的一般保護。

您會這樣做的可能原因有：

-   若要要確保所有使用者都可以從他們的行動裝置開啟檔案。

-   若要要確保所有沒有支援原生保護之應用程式的使用者都可以開啟檔案。

-   若要配合會依檔案副檔名而採取動作的安全性系統，也可以重新設定系數以配合 .pfile 副檔名，但無法重新設定以配合原生保護的多個副檔名。

同樣地，您可以強制 RMS 共用應用程式對預設會套用一般保護的檔案套用原生保護。 這可能適用於您有支援 RMS API的應用程式的情況 – 例如，內部開發人員所撰寫的企業營運應用程式或向獨立軟體廠商 (ISV) 購買的應用程式。

您也可以強制 RMS 共用應用程式封鎖檔案的保護 (不套用原生保護或一般保護)。 例如，當您有必須能夠開啟特定檔案來處理其內容的自動化應用程式或服務，可能有此需要。 當您封鎖某個檔案類型的保護時，使用者無法使用 RMS 共用應用程式來保護該檔案類型的檔案。 當他們嘗試保護檔案時，會看到訊息指出管理員已防止保護，且他們必須取消其保護檔案的動作。

若要設定 RMS 共用應用程式對預設會套用原生保護的檔案套用一般保護，請進行以下登錄編輯：

1.  **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection**:建立名為 **&#42;** 的新機碼。

    此設定表示具有任何副檔名的檔案。

2.  在新加入的機碼 **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\&#42;** 中，建立 (REG_SZ) 名為 **Encryption** 的新字串值，且其資料值為 **Pfile**。

    這項設定會導致 RMS 共用應用程式套用一般保護。

這兩項設定會導致 RMS 共用應用程式對所有有副檔名的檔案套用一般保護。 如果這是您的目標，則不需要進一步的設定。 不過，您可以定義特定檔案類型的例外狀況，讓它們仍然受到原生保護。 若要這樣做，您必須為每種檔案類型進行三個額外的登錄編輯：

1.  **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection**:加入包含該檔案副檔名 (不含前面的點) 的新機碼。

    例如，為副檔名為 .docx 的檔案建立 **DOCX** 機碼。

2.  在新加入的檔案類型機碼中 (例如，**HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\DOCX**)，建立名為 **AllowPFILEEncryption** 的新 DWORD 值，且設定其值為 **0**。

3.  在新加入的檔案類型機碼中 (例如，**HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\DOCX**)，建立名為 **Encryption** 的新字串值，且設定其值為 **Native**。

進行這些設定後，所有檔案會受到一般保護，但 .docx 副檔名的檔案除外，後者會受到 RMS 共用應用程式的原生保護。

針對您想要定義為例外狀況的其他檔案類型重複這三個步驟，因為它們支援原生保護，而您不要它們受 RMS 共用應用程式的一般保護。

您可以變更 **Encryption** 字串的值，為其他案例進行類似登錄編輯，此字串支援下列值：

-   **Pfile**：一般保護

-   **Native**：原生保護

-   **Off**：封鎖保護

## 請參閱
[Rights Management 共用應用程式使用者指南 &#40;英文&#41;](../Topic/Rights_Management_sharing_application_user_guide.md)

