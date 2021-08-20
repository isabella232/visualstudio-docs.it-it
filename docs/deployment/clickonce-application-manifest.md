---
title: ClickOnce Manifesto dell'applicazione | Microsoft Docs
description: Informazioni sul ClickOnce dell'applicazione, ovvero un file XML che descrive un'applicazione distribuita tramite ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- application manifests [ClickOnce]
- ClickOnce, application manifests
ms.assetid: 29570cec-4e53-4660-a850-abc4fa150243
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 421f48615cc46e401d9cd982f66c735807c403c6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160894"
---
# <a name="clickonce-application-manifest"></a>Manifesto dell'applicazione ClickOnce
Un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto dell'applicazione è un file XML che descrive un'applicazione distribuita tramite [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] I manifesti dell'applicazione hanno gli elementi e gli attributi seguenti.

| Elemento | Descrizione | Attributi |
| - | - | - |
| [\<assembly> Elemento](../deployment/assembly-element-clickonce-application.md) | Obbligatorio. Elemento di primo livello. | `manifestVersion` |
| [\<assemblyIdentity> Elemento](../deployment/assemblyidentity-element-clickonce-application.md) | Obbligatorio. Identifica l'assembly primario [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione. | `name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language` |
| [\<trustInfo> Elemento](../deployment/trustinfo-element-clickonce-application.md) | Identifica i requisiti di sicurezza dell'applicazione. | Nessuno |
| [\<entryPoint> Elemento](../deployment/entrypoint-element-clickonce-application.md) | Obbligatorio. Identifica il punto di ingresso del codice dell'applicazione. | `name` |
| [\<dependency> Elemento](../deployment/dependency-element-clickonce-application.md) | Obbligatorio. Identifica ogni dipendenza necessaria per l'esecuzione dell'applicazione. Può anche identificare gli assembly che è necessario preinstallare. | Nessuno |
| [\<file> Elemento](../deployment/file-element-clickonce-application.md) | facoltativo. Identifica ogni file non assembly utilizzato dall'applicazione. Può includere i dati sull'isolamento COM (Component Object Model) associati al file. | `name`<br /><br /> `size`<br /><br /> `group`<br /><br /> `optional`<br /><br /> `writeableType` |
| [\<fileAssociation> Elemento](../deployment/fileassociation-element-clickonce-application.md) | facoltativo. Identifica un'estensione di file da associare all'applicazione. | `extension`<br /><br /> `description`<br /><br /> `progid`<br /><br /> `defaultIcon` |

## <a name="remarks"></a>Commenti
 Il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] file manifesto dell'applicazione identifica un'applicazione distribuita tramite [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Per altre informazioni su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], vedere [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md).

## <a name="file-location"></a>Percorso del file
 Un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto dell'applicazione è specifico di una singola versione di una distribuzione. Per questo motivo, devono essere archiviati separatamente dai manifesti di distribuzione. La convenzione comune è di posizionarli in una sottodirectory denominata in base alla versione associata.

 Il manifesto dell'applicazione deve sempre essere firmato prima della distribuzione. Se si modifica manualmente un manifesto dell'applicazione, è necessario usare *mage.exe* per firmare nuovamente il manifesto dell'applicazione, aggiornare il manifesto della distribuzione e quindi firmare nuovamente il manifesto della distribuzione. Per altre informazioni, vedere [Procedura dettagliata: Distribuire manualmente un'ClickOnce applicazione](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="file-name-syntax"></a>Sintassi del nome file
 Il nome di un file manifesto dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] deve essere composto dal nome completo e dall'estensione dell'applicazione come identificati nell'elemento `assemblyIdentity`, seguiti dall'estensione *manifest*. Ad esempio, un manifesto dell'applicazione che fa riferimento *Example.exe'applicazione* userà la sintassi del nome file seguente.

 `example.exe.manifest`

## <a name="example"></a>Esempio
 L'esempio di codice seguente mostra un manifesto dell'applicazione per [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] un'applicazione.

```xml
<?xml version="1.0" encoding="utf-8"?>
<asmv1:assembly xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd" manifestVersion="1.0" xmlns:asmv3="urn:schemas-microsoft-com:asm.v3" xmlns:dsig="http://www.w3.org/2000/09/xmldsig#" xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2" xmlns="urn:schemas-microsoft-com:asm.v2" xmlns:asmv1="urn:schemas-microsoft-com:asm.v1" xmlns:asmv2="urn:schemas-microsoft-com:asm.v2" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">
  <asmv1:assemblyIdentity name="My Application Deployment.exe" version="1.0.0.0" publicKeyToken="43cb1e8e7a352766" language="neutral" processorArchitecture="x86" type="win32" />
  <application />
  <entryPoint>
    <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />
    <commandLine file="MyApplication.exe" parameters="" />
  </entryPoint>
  <trustInfo>
    <security>
      <applicationRequestMinimum>
        <PermissionSet Unrestricted="true" ID="Custom" SameSite="site" />
        <defaultAssemblyRequest permissionSetReference="Custom" />
      </applicationRequestMinimum>
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">
        <!--
          UAC Manifest Options
          If you want to change the Windows User Account Control level replace the
          requestedExecutionLevel node with one of the following.

        <requestedExecutionLevel  level="asInvoker" uiAccess="false" />
        <requestedExecutionLevel  level="requireAdministrator" uiAccess="false" />
        <requestedExecutionLevel  level="highestAvailable" uiAccess="false" />

         If you want to utilize File and Registry Virtualization for backward
         compatibility then delete the requestedExecutionLevel node.
    -->
        <requestedExecutionLevel level="asInvoker" uiAccess="false" />
      </requestedPrivileges>
    </security>
  </trustInfo>
  <dependency>
    <dependentOS>
      <osVersionInfo>
        <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
      </osVersionInfo>
    </dependentOS>
  </dependency>
  <dependency>
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
      <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.20506.0" />
    </dependentAssembly>
  </dependency>
  <dependency>
    <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="4096">
      <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />
      <hash>
        <dsig:Transforms>
          <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
        </dsig:Transforms>
        <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
        <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>
      </hash>
    </dependentAssembly>
  </dependency>
<publisherIdentity name="CN=DOMAINCONTROLLER\UserMe" issuerKeyHash="18312a18a21b215ecf4cdb20f5a0e0b0dd263c08" /><Signature Id="StrongNameSignature" xmlns="http://www.w3.org/2000/09/xmldsig#">
...
</Signature></r:issuer></r:license></msrel:RelData></KeyInfo></Signature></asmv1:assembly>
```

## <a name="see-also"></a>Vedi anche
- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)