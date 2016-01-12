---
description: na
keywords: na
title: Active Directory Rights Management Services Mobile Device Extension
search: na
ms.date: na
ms.tgt_pltfrm: na
ms.assetid: a69ead9d-7dd3-4b38-9830-4728e9757341
robots: noindex,nofollow
---
# Active Directory Rights Management Services 行動裝置擴充功能
Active Directory Rights Management Services (AD RMS) 行動裝置延伸模組是在現有的 AD RMS 部署上執行。這可讓擁有行動裝置的使用者在其裝置支援最新的 RMS 用戶端，並使用 RMS 架構應用程式時，保護和取用機密資料。例如，這些裝置的使用者可以執行以下操作：

-   使用 RMS 共用應用程式取用不同格式 (包括 .txt、.csv 和 .xml) 的受保護文字檔案。

-   使用 RMS 共用應用程式取用受保護的影像檔 (包括 .jpg、.gif 和 .tif)。

-   使用 RMS 共用應用程式開啟以一般方式保護的任何檔案 (.pfile 格式)。

-   使用 RMS 共用應用程式保護裝置上的影像檔。

-   使用 RMS 架構的 PDF 檢視器，讓行動裝置開啟使用適用於 Windows 的 RMS 共用應用程式或其他 RMS 架構應用程式保護的 PDF 檔。

-   使用軟體廠商的其他應用程式，這些應用程式可提供支援原生支援 RMS 之檔案類型的 RMS 架構應用程式。

-   使用透過 RMS SDK 撰寫之內部開發的 RMS 架構應用程式。

> [!NOTE]
> 您可以從 Microsoft 網站上的 [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) 頁面，下載 RMS 共用應用程式。
> 
> 如需有關 RMS 支援的不同檔案類型的詳細資訊，請參閱《Rights Management 共用應用程式系統管理員指南》中的[支援的檔案類型和副檔名](http://technet.microsoft.com/library/dn339003.aspx)一節。

如果使用支援 Exchange ActiveSync IRM 的電子郵件應用程式，就不需要使用行動裝置擴充功能在裝置上取用或撰寫受保護的電子郵件。對於 RMS 和行動裝置的這項支援是與 Exchange 2010 Service Pack 1 一起推出。

使用下列各節部署 Active Directory Rights Management Services (AD RMS) 行動裝置擴充功能：

-   [AD RMS 行動裝置擴充功能的先決條件](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_Preqs)

    -   [為 AD RMS 行動裝置擴充功能設定 AD FS](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_ADFS)

    -   [為 AD RMS 行動裝置擴充功能設定 AD FS](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_ADFS)

-   [為 AD RMS 行動裝置擴充功能指定 DNS SRV 記錄](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_SRV)

-   [部署 AD RMS 行動裝置擴充功能](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_Deploy)

## <a name="BKMK_Preqs"></a>AD RMS 行動裝置擴充功能的先決條件
安裝 AD RMS 行動裝置擴充功能之前，請確定這些相依性已就緒。

|需求|其他資訊|
|------|--------|
|現有的 AD RMS 部署在 Windows Server 2012 R2 或 Windows Server 2012 上。 **Note:** AD RMS 必須在另一部伺服器上使用完整的 Microsoft SQL Server 型資料庫，而不是在相同伺服器上通常用於測試的 Windows 內部資料庫。|如需有關 AD RMS 的文件，請參閱 Windows Server 文件庫中的 [Active Directory Rights Management Services](http://technet.microsoft.com/library/hh831364.aspx)。|
|AD FS 部署在 Windows Server 2012 R2 上|如需有關 AD FS 的文件，請參閱 Windows Server 文件庫中的 [Windows Server 2012 R2 AD FS 部署指南](http://technet.microsoft.com/library/dn486820.aspx)。<br /><br />必須為行動裝置擴充功能設定 AD FS。如需指示，請參閱本主題中的[為 AD RMS 行動裝置擴充功能設定 AD FS](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_ADFS)一節。|
|DNS 中的 SRV 記錄|在您公司的一或多個網域中建立一或多筆 SRV 記錄：<br /><br />-   一筆記錄供使用者將會使用的每個電子郵件網域尾碼使用<br />-   一筆記錄供您的 RMS 叢集為保護內容所使用的每個 FQDN 使用<br /><br />當使用者從其行動裝置提供他們的電子郵件地址時，網域尾碼用來識別應該使用 AD RMS 基礎結構還是 Azure RMS。找到 SRV 記錄時，就會將用戶端重新導向至回應該 URL 的 AD RMS 伺服器。<br /><br />當使用者使用行動裝置取用受保護的內容時，用戶端應用程式會查詢 DNS 是否有符合保護內容之叢集的 URL 中的 FQDN 的記錄。接著，裝置會導向至 DNS 記錄中指定的 AD RMS 叢集，並取得開啟內容的授權。在大部分情況下，RMS 叢集將會是保護內容的相同 RMS 叢集。<br /><br />如需有關如何指定 SRV 記錄的資訊，請參閱本主題中的[為 AD RMS 行動裝置擴充功能指定 DNS SRV 記錄](../Topic/Active_Directory_Rights_Management_Services_Mobile_Device_Extension.md#BKMK_SRV)一節。|
|目前支援的用戶端：<br /><br />-   使用適用於 Android 的最新版 RMS 共用應用程式的 Android 裝置|最低版本為 Android 4.0.3。<br /><br />從 [Microsoft Connect 網站](https://connect.microsoft.com/site1170/Downloads)下載適用於 Android 的 RMS 共用應用程式並側載到裝置。|

### <a name="BKMK_ADFS"></a>為 AD RMS 行動裝置擴充功能設定 AD FS
您必須先設定 AD FS，然後再授權適用於 Android 的 RMS 共用應用程式。

##### 步驟 1：設定 AD FS

-   您可以執行 Windows PowerShell 指令碼來自動設定 AD FS，以支援 AD RMS 行動裝置擴充功能，或者您可以手動指定設定選項和值：

    -   若要自動設定 AD FS，請將下列複製並貼到 Windows PowerShell 指令碼檔案，然後執行：

        ```
        # This Script Configures the Microsoft Rights Management Mobile Device Extension and Claims used in the ADFS Server

        # Check if Microsoft Rights Management Mobile Device Extension is configured on the Server 
        $CheckifConfigured = Get-AdfsRelyingPartyTrust -Identifier "api.rms.rest.com"
        if ($CheckifConfigured)
        {
        Write-Host "api.rms.rest.com Identifer used for Microsoft Rights Management Mobile Device Extension is already configured on this Server"
        Write-Host $CheckifConfigured 
        }
        else
        {
        Write-Host "Configuring  Microsoft Rights Management Mobile Device Extension "

        # TransformaRules used by Microsoft Rights Management Mobile Device Extension
        # Claims: E-mail, UPN and ProxyAddresses
        $TransformRules = @"
        @RuleTemplate = "LdapClaims"
        @RuleName = "Jwt Token"
        c:[Type ==
        "http://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname",
        Issuer == "AD AUTHORITY"]
         => issue(store = "Active Directory", types =
        ("http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress",
        "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn",
        "http://schemas.xmlsoap.org/claims/ProxyAddresses"), query =
        ";mail,userPrincipalName,proxyAddresses;{0}", param = c.Value);

        @RuleTemplate = "PassThroughClaims"
        @RuleName = "JWT pass through"
        c:[Type == "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress"]
         => issue(claim = c);

        @RuleTemplate = "PassThroughClaims"
        @RuleName = "JWT pass through"
        c:[Type == "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn"]
         => issue(claim = c);

        @RuleTemplate = "PassThroughClaims"
        @RuleName = "JWT pass through Proxy addresses"
        c:[Type == "http://schemas.xmlsoap.org/claims/ProxyAddresses"]
         => issue(claim = c);
        "@

        # AuthorizationRules used by Microsoft Rights Management Mobile Device Extension
        # Allow All users
        $AuthorizationRules = @"
        @RuleTemplate = "AllowAllAuthzRule"
         => issue(Type = "http://schemas.microsoft.com/authorization/claims/permit",
        Value = "true");
        "@

        # Add a Relying Part Truest with Name -"Microsoft Rights Management Mobile Device Extension" Identifier "api.rms.rest.com"
        Add-ADFSRelyingPartyTrust -Name "Microsoft Rights Management Mobile Device Extension" -Identifier "api.rms.rest.com" -IssuanceTransformRules $TransformRules -IssuanceAuthorizationRules  $AuthorizationRules

        Write-Host "Microsoft Rights Management Mobile Device Extension Configured"
        }
        ```

    -   若要手動設定 AD FS，請使用以下設定：

        |設定|值|
        |------|-----|
        |**信賴憑證者信任**|api.rms.rest.com|
        |**宣告規則**|[屬性存放區]：Active Directory<br /><br />[電子郵件地址]：電子郵件地址<br /><br />[使用者主體名稱]：UPN<br /><br />[Proxy 位址]：https://schemas.xmlsoap.org/claims/ProxyAddresses|

##### 步驟 2：授權適用於 Android 的 RMS 共用應用程式

-   執行下列 Windows PowerShell 命令以增加 Android 裝置的支援：

    ```
    Add-AdfsClient -Name "RMSsharingAndroid" -ClientId "com.microsoft.ipviewer" -RedirectUri @("com.microsoft.ipviewer://authorize")
    ```

### <a name="BKMK_SRV"></a>為 AD RMS 行動裝置擴充功能指定 DNS SRV 記錄
您必須為您的使用者使用的每個電子郵件網域建立 DNS SRV 記錄。如果您的使用者使用單一父網域的子網域，而且這個連續的命名空間中的所有使用者使用相同的 RMS 叢集，您可以在父網域中，只使用一筆 SRV 記錄，RMS 就會尋找適當的 DNS 記錄。

SRV 記錄的格式如下：_rmsdisco._http._tcp. *&lt;emailsuffix&gt;**&lt;portnumber&gt;**&lt;RMSClusterFQDN&gt;*

例如，如果您的組織有下列電子郵件地址的使用者：

-   user@contoso.com

-   user@sales.contoso.com

-   user@fabrikam.com

，而且對於 contoso.com，沒有使用名稱不同於 **rmsserver.contoso.com** 之 RMS 叢集的其他子網域，請建立兩個具有以下這些值的 DNS SRV 記錄：

-   _rmsdisco._http._tcp.contoso.com 443 rmsserver.contoso.com

-   _rmsdisco._http._tcp.fabrikam.com 443 rmsserver.contoso.com

除了用於您的電子郵件網域的這些 DNS SRV 記錄之外，您還必須在使用者網域中建立另一個 DNS SRV 記錄。此記錄必須指定保護內容之 RMS 叢集的 URL。受 RMS 保護的每個檔案都包含保護該檔案之叢集的 URL。行動裝置使用 DNS SRV 記錄，以及記錄中指定的 URL FQDN 尋找可支援行動裝置的對應 RMS 叢集。

例如，如果您的 RMS 叢集是 **rmsserver.contoso.com**，請建立具有以下值的 DNS SRV 記錄：**_rmsdisco._http._tcp.rmsserver.contoso.com 443 rmsserver.contoso.com**

## <a name="BKMK_Deploy"></a>部署 AD RMS 行動裝置擴充功能
安裝 AD RMS 行動裝置擴充功能之前，請確定已符合上一節的先決條件，而且您知道您的 AD FS 伺服器的 URL。然後執行下列動作：

1.  從 [Microsoft Connect 網站](http://go.microsoft.com/fwlink/?LinkId=397245)下載 AD RMS 行動裝置擴充功能。

2.  執行 Setup.exe 以啟動 [Active Directory Rights Management Services 行動裝置擴充功能安裝精靈]。

3.  出現提示時，輸入您先前設定之 AD FS 伺服器的 URL。

4.  完成精靈。

在您的 RMS 叢集的所有節點上執行此精靈。

