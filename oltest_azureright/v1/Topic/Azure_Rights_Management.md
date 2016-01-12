---
description: na
keywords: na
title: Azure Rights Management
search: na
ms.date: na
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 965581c8-be3c-43b4-8145-5cefd29c7636
---
# Azure Rights Management
<?xml version="1.0" encoding="utf-8"?>
<caps:SxS xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
  <caps:SxSTarget locale="zh-TW">
    <developerConceptualDocument xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd" xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <introduction>
        <para>
          <caps:sentence sentenceid="62b83eea4fc0746f132ff6c8d4a52b84" id="tgt1" class="tgtSentence">本頁面介紹 Microsoft <token>aad_rightsmanagement_1</token> (Azure RMS) 的技術文件集，協助保護貴組織的敏感資料，防止未授權的存取行為，並控管資訊的使用方式。</caps:sentence>
          <caps:sentence sentenceid="23b58def11b45727d3351702515f86af" id="tgt2" class="tgtSentence">
            <token>aad_rightsmanagement_1</token> 是一項雲端服務，並且已整合至 Office 365 及 Azure Active Directory 等其他 Microsoft 雲端服務和應用程式中。</caps:sentence>
          <caps:sentence sentenceid="145e719c453fbadadee79768f74667aa" id="tgt3" class="tgtSentence"> 然而，您仍然可以在內部部署應用程式和服務中使用這項服務。</caps:sentence>
        </para>
        <para>
          <caps:sentence sentenceid="c6fa2923fc013e88430215867fa3b41f" id="tgt4" class="tgtSentence">
            <token>aad_rightsmanagement_2</token> 使用加密、身分識別及授權原則來協助保護您的檔案和電子郵件。</caps:sentence>
          <caps:sentence sentenceid="6cee999ea54670dc3aaf3fa7bfdf7566" id="tgt5" class="tgtSentence"> 與標準存取控制 (例如 NTFS 權限) 相比，使用 <token>aad_rightsmanagement_2</token> 所套用的保護會跟著檔案和電子郵件，不受位置影響 – 不論是在貴組織內部或外部、網路、檔案伺服器及應用程式。</caps:sentence>
          <caps:sentence sentenceid="3cea98f77e893eb1025f89567a366d77" id="tgt6" class="tgtSentence"> 此資訊保護解決方案可讓您在與他人共用資料的情況下，依然能控管資料。</caps:sentence>
        </para>
        <para>
          <caps:sentence sentenceid="3d1e430f66ef0a41b3c0d4361753146d" id="tgt7" class="tgtSentence">例如，您可以設定讓檔案僅供貴組織中的人員存取，或是控制檔案是否可供編輯、限制成唯讀或防止列印。</caps:sentence>
          <caps:sentence sentenceid="a1d4b6ea938e5c3193bcc436be24f8c0" id="tgt8" class="tgtSentence"> 您也可以使用類似方式設定電子郵件，此外，還可以防止它們被轉寄或防止使用 [全部回覆] 選項。</caps:sentence>
          <caps:sentence sentenceid="76c61c663112d6aabc8b0558688c8514" id="tgt9" class="tgtSentence"> 只要使用標準化原則範本，即可簡化這些保護工作並使工作變得有效率。</caps:sentence>
        </para>
        <para>
          <caps:sentence sentenceid="31d23eeb49a60f86a1641f17c6570b72" id="tgt10" class="tgtSentence">
      如需更深入的了解和範例，請參閱 <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df">What is Azure Rights Management?</link></caps:sentence>
        </para>
        <para>
          <caps:sentence sentenceid="0d618ca3ca5b0a48f105c1e37165a023" id="tgt11" class="tgtSentence">使用下列資訊可深入了解 <token>aad_rightsmanagement_1</token> 及為貴組織部署這項服務：</caps:sentence>
        </para>
        <list class="bullet">
          <listItem>
            <para>
              <link xlink:href="5214667c-ec69-42ca-8bbf-8cb22da8c62e">Getting started with Azure AD Rights Management</link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="206a0bfe-0912-4e0e-aa15-484b000b264c">Configuring rights management</link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="18564e4a-9364-4ed2-8f17-89d24fc0d878">Using rights management</link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="a890e04a-4b70-41b5-8d5f-3c210a669faa">Administering rights management</link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="c994d616-cff6-4930-9228-a7f7d198a160">Rapid Deployment Guide for Azure Rights Management</link>
            </para>
          </listItem>
        </list>
        <para>
          <caps:sentence sentenceid="8f8764b84fbfe3fb41a1de8bd2151a22" id="tgt12" class="tgtSentence">如需其他資源，請參閱 <link xlink:href="7cc73d92-27d6-49ff-a8ab-2fae73519b4b">Information and Support for Azure Rights Management</link>。</caps:sentence>
        </para>
      </introduction>
      <section>
        <title>
          <caps:sentence sentenceid="b75b1651ff8c1f6e857670d70de57727" id="tgt13" class="tgtSentence">也稱為...</caps:sentence>
        </title>
        <content>
          <para>
            <caps:sentence sentenceid="0bb50d5ace4abd536a35235fd9cca548" id="tgt14" class="tgtSentence">Azure Rights Management 亦稱為 <legacyItalic>Azure Rights Management 服務</legacyItalic>，但因為它在 Azure 中以服務方式執行，所以名稱中通常省略「服務」二字。</caps:sentence>
            <caps:sentence sentenceid="4ec4858d185533976ae0410b2d35079b" id="tgt15" class="tgtSentence"> 這是雲端版本的 <legacyItalic>Active Directory Rights Management Services</legacyItalic> (AD RMS)，最初發行時稱為 <legacyItalic>Windows Rights Management Services</legacyItalic> (Windows RMS)。</caps:sentence>
          </para>
          <para>
            <caps:sentence sentenceid="0726a4db7b39858b6c4062cb42e94fe2" id="tgt16" class="tgtSentence">因為 RMS 在其先前版本中已是慣用縮寫，所以 Azure Rights Management 通常縮寫為 <legacyItalic>Azure RMS</legacyItalic>。</caps:sentence>
          </para>
          <para>
            <caps:sentence sentenceid="951d003f6152823990af843b34aa46e3" id="tgt17" class="tgtSentence">Azure Rights Management 最初稱為 <legacyItalic>Windows Azure Active Directory Rights Management</legacyItalic> (通常縮寫為 <legacyItalic>Windows Azure AD Rights Management</legacyItalic>)，後來改為 <legacyItalic>Windows Azure Rights Management</legacyItalic>，現在確定為 <legacyItalic>Azure Rights Management</legacyItalic>。</caps:sentence>
          </para>
          <para>
            <caps:sentence sentenceid="ae8b2b285d98ab9534ef325989bd0813" id="tgt18" class="tgtSentence">您也可能會看到提及 <legacyItalic>Information Rights Management</legacyItalic>，通常縮寫為 <legacyItalic>IRM</legacyItalic>。</caps:sentence>
            <caps:sentence sentenceid="bcf8f7f6e8efe34a2816544f253dc99e" id="tgt19" class="tgtSentence"> 這是 Office 的 Rights Management 實作，可以支援 Azure RMS 與 AD RMS。</caps:sentence>
            <caps:sentence sentenceid="814cd385574d9159ca8935f57babd54f" id="tgt20" class="tgtSentence">  Azure RMS 最初發行時只能搭配 Office 365 一起使用 - 例如，與 Office 365 E3 訂用帳戶一起使用。</caps:sentence>
            <caps:sentence sentenceid="21c6900dba0d93d29042f515dd3cd695" id="tgt21" class="tgtSentence"> 現在，Azure RMS 已擴充到其他訂用帳戶，例如 Enterprise Mobility Suite (EMS)，目前的支援包括 Office 2016、Office 2013、Office 2010、內部部署版本的 SharePoint 和 Exchange，而且 Azure RMS 可以保護任何檔案類型。</caps:sentence>
            <caps:sentence sentenceid="3ce055386165dac9a926371c350ecfed" id="tgt22" class="tgtSentence"> 如需詳細資訊，請參閱<link xlink:href="2cdc7bde-4044-4021-b887-11476f99afd9">How Applications Support Azure Rights Management</link>。</caps:sentence>
          </para>
          <para>
            <caps:sentence sentenceid="483562e5c3f5a51c6ece6ac16a3e8b0f" id="tgt23" class="tgtSentence">您也可能會看到偶爾提及 <legacyItalic>Microsoft Rights Management</legacyItalic> 或 <legacyItalic>Microsoft Rights Management 服務</legacyItalic>，這是同時涵蓋 Azure RMS 與 AD RMS 的統稱。</caps:sentence>
            <caps:sentence sentenceid="62590b7cc80fa58960258871f90025a1" id="tgt24" class="tgtSentence">  "<legacyItalic>NEW Microsoft RMS</legacyItalic>" 是 Azure Rights Management 正式發行時偶爾使用的熱門標籤，用以強調新版本的部署比先前的內部部署版本更簡單。</caps:sentence>
          </para>
          <alert class="tip">
            <para>
              <caps:sentence sentenceid="da41105f4520ac7aa5ba99aad81c8f23" id="tgt25" class="tgtSentence">您可以在 <link xlink:href="742877bf-26f5-40e3-b1f7-8475e7c3ce11">Terminology for Azure Rights Management</link>中找到這些術語 (還有其他)。</caps:sentence>
            </para>
          </alert>
          <para>
            <caps:sentence sentenceid="d2584214cdff2107001a9881c3f0d321" id="tgt26" class="tgtSentence">Microsoft Rights Management 服務作為企業資訊保護解決方案，不提供通常用以防止非法散佈數位軟體的數位版權管理 (DRM) 解決方案。</caps:sentence>
          </para>
        </content>
      </section>
      <relatedTopics></relatedTopics>
    </developerConceptualDocument>
  </caps:SxSTarget>
  <caps:SxSSource locale="en-US">
    <developerConceptualDocument xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd" xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <introduction>
        <para>
          <caps:sentence id="src1" class="srcSentence">This page introduces the technical documentation set for Microsoft <token>aad_rightsmanagement_1</token> (Azure RMS), to help you protect your organization’s sensitive information from unauthorized access, and control how this information is used.</caps:sentence>
          <caps:sentence id="src2" class="srcSentence">
            <token>aad_rightsmanagement_1</token> is a cloud service, and is integrated into other Microsoft cloud services and applications, such as Office 365 and Azure Active Directory.</caps:sentence>
          <caps:sentence id="src3" class="srcSentence"> However, it can also be used with your on-premises applications and services.</caps:sentence>
        </para>
        <para>
          <caps:sentence id="src4" class="srcSentence">
            <token>aad_rightsmanagement_2</token> uses encryption, identity, and authorization policies to help secure your files and email.</caps:sentence>
          <caps:sentence id="src5" class="srcSentence"> In comparison to standard access controls, such as NTFS permissions, protection that is applied by using <token>aad_rightsmanagement_2</token> stays with the files and emails, independently of the location—inside or outside your organization, networks, file servers, and applications.</caps:sentence>
          <caps:sentence id="src6" class="srcSentence"> This information protection solution keeps you in control of your data, even when it is shared with other people.</caps:sentence>
        </para>
        <para>
          <caps:sentence id="src7" class="srcSentence">For example, you can configure a file so that it can be accessed only by people in your organization, or control whether the file can be edited, or restricted to read-only, or prevent it from being printed.</caps:sentence>
          <caps:sentence id="src8" class="srcSentence"> You can configure emails similarly, and in addition, prevent them from being forwarded or prevent the use of the Reply All option.</caps:sentence>
          <caps:sentence id="src9" class="srcSentence"> These protection tasks can be simplified and streamlined by using standardized policy templates.</caps:sentence>
        </para>
        <para>
          <caps:sentence id="src10" class="srcSentence">
      For a deeper understanding and some examples, see <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df">What is Azure Rights Management?</link></caps:sentence>
        </para>
        <para>
          <caps:sentence id="src11" class="srcSentence">Use the following information to learn more about <token>aad_rightsmanagement_1</token> and deploy it for your organization:</caps:sentence>
        </para>
        <list class="bullet">
          <listItem>
            <para>
              <link xlink:href="5214667c-ec69-42ca-8bbf-8cb22da8c62e">Getting started with Azure AD Rights Management</link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="206a0bfe-0912-4e0e-aa15-484b000b264c">Configuring rights management</link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="18564e4a-9364-4ed2-8f17-89d24fc0d878">Using rights management</link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="a890e04a-4b70-41b5-8d5f-3c210a669faa">Administering rights management</link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="c994d616-cff6-4930-9228-a7f7d198a160">Rapid Deployment Guide for Azure Rights Management</link>
            </para>
          </listItem>
        </list>
        <para>
          <caps:sentence id="src12" class="srcSentence">For additional resources, see <link xlink:href="7cc73d92-27d6-49ff-a8ab-2fae73519b4b">Information and Support for Azure Rights Management</link>.</caps:sentence>
        </para>
      </introduction>
      <section>
        <title>
          <caps:sentence id="src13" class="srcSentence">Also known as ...</caps:sentence>
        </title>
        <content>
          <para>
            <caps:sentence id="src14" class="srcSentence">Azure Rights Management is also known as <legacyItalic>Azure Rights Management service</legacyItalic>, but because it runs as a service in Azure, the "service" is often omitted from its name.</caps:sentence>
            <caps:sentence id="src15" class="srcSentence"> It is the cloud version of <legacyItalic>Active Directory Rights Management Services</legacyItalic> (AD RMS), which was first released as <legacyItalic>Windows Rights Management Services</legacyItalic> (Windows RMS).</caps:sentence>
          </para>
          <para>
            <caps:sentence id="src16" class="srcSentence">Because RMS is a well-known abbreviation for its predecessors, Azure Rights Management is often abbreviated to <legacyItalic>Azure RMS</legacyItalic>.</caps:sentence>
          </para>
          <para>
            <caps:sentence id="src17" class="srcSentence">Azure Rights Management was originally named <legacyItalic>Windows Azure Active Directory Rights Management</legacyItalic> (often abbreviated to <legacyItalic>Windows Azure AD Rights Management</legacyItalic>), then  <legacyItalic>Windows Azure Rights Management</legacyItalic>, and now finally <legacyItalic>Azure Rights Management</legacyItalic>.</caps:sentence>
          </para>
          <para>
            <caps:sentence id="src18" class="srcSentence">You might also see references to <legacyItalic>Information Rights Management,</legacyItalic> often abbreviated to <legacyItalic>IRM</legacyItalic>.</caps:sentence>
            <caps:sentence id="src19" class="srcSentence"> This is the Office implementation of Rights Management, which can support both Azure RMS and AD RMS.</caps:sentence>
            <caps:sentence id="src20" class="srcSentence">  When Azure RMS was first released, it could only be used with Office 365—for example, with an Office 365 E3 subscription.</caps:sentence>
            <caps:sentence id="src21" class="srcSentence"> Now, Azure RMS  is extended to other subscriptions, such as the Enterprise Mobility Suite (EMS) and support now includes Office 2016, Office 2013, Office 2010, on-premises versions of SharePoint and Exchange, and Azure RMS can protect any file type.</caps:sentence>
            <caps:sentence id="src22" class="srcSentence"> For more information, see  <link xlink:href="2cdc7bde-4044-4021-b887-11476f99afd9">How Applications Support Azure Rights Management</link>.</caps:sentence>
          </para>
          <para>
            <caps:sentence id="src23" class="srcSentence">You might also see occasional references to <legacyItalic>Microsoft Rights Management</legacyItalic>, or <legacyItalic>Microsoft Rights Management services</legacyItalic>, which is a collective term that can include both Azure RMS and AD RMS.</caps:sentence>
            <caps:sentence id="src24" class="srcSentence">  The "<legacyItalic>NEW Microsoft RMS</legacyItalic>" was a popular label that was sometimes used  when Azure Rights Management was officially released, to emphasize the new ease of deployment in comparison to its on-premises predecessors.</caps:sentence>
          </para>
          <alert class="tip">
            <para>
              <caps:sentence id="src25" class="srcSentence">You'll find these terms (and more) in <link xlink:href="742877bf-26f5-40e3-b1f7-8475e7c3ce11">Terminology for Azure Rights Management</link>.</caps:sentence>
            </para>
          </alert>
          <para>
            <caps:sentence id="src26" class="srcSentence">As an enterprise information protection solution, Microsoft Rights Management services do not provide digital rights management (DRM) solutions that typically protect against illegal distribution of digital software.</caps:sentence>
          </para>
        </content>
      </section>
      <relatedTopics></relatedTopics>
    </developerConceptualDocument>
  </caps:SxSSource>
</caps:SxS>