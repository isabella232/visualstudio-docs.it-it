---
title: URL di supporto per i prerequisiti nella ClickOnce distribuzione
description: Informazioni su come ClickOnce di distribuzione dei prerequisiti per l'ClickOnce'applicazione e come la distribuzione gestisce i prerequisiti mancanti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- ClickOnce deployment, URLs
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 048d379aa3194eb7e6fca46019e6c5a2ddbd60c5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122035813"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Procedura: Specificare un URL di supporto per i singoli prerequisiti in una distribuzione ClickOnce
Una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione può testare una serie di prerequisiti che devono essere disponibili nel computer client per [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] l'esecuzione dell'applicazione. Queste dipendenze includono la versione minima richiesta del .NET Framework, la versione del sistema operativo e tutti gli assembly che devono essere preinstallati nella Global Assembly Cache (GAC). [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], tuttavia, non può installare uno di questi prerequisiti. Se non viene trovato un prerequisito, interrompe semplicemente l'installazione e visualizza una finestra di dialogo che spiega perché l'installazione non è riuscita.

 Esistono due metodi per installare i prerequisiti. È possibile installarli usando un'applicazione del programma di avvio automatico. In alternativa, è possibile specificare un URL di supporto per i singoli prerequisiti, che viene visualizzato agli utenti nella finestra di dialogo se il prerequisito non viene trovato. La pagina a cui fa riferimento tale URL può contenere collegamenti a istruzioni per l'installazione del prerequisito richiesto. Se un'applicazione non specifica un URL di supporto per un singolo prerequisito, visualizza l'URL di supporto specificato nel manifesto della distribuzione per l'intera applicazione, se [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] definito.

 Mentre ,Mage.exeeMageUI.exepossono essere tutti usati per generare distribuzioni, nessuno di questi strumenti supporta direttamente la specifica di un URL di supporto per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i singoli **  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] prerequisiti. Questo documento descrive come modificare il manifesto dell'applicazione e il manifesto della distribuzione per includere questi URL di supporto.

### <a name="specify-a-support-url-for-an-individual-prerequisite"></a>Specificare un URL di supporto per un singolo prerequisito

1. Aprire il manifesto dell'applicazione (file *con estensione manifest)* per [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] l'applicazione in un editor di testo.

2. Per un prerequisito del sistema operativo, aggiungere `supportUrl` l'attributo `dependentOS` all'elemento :

   ```xml
    <dependency>
       <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">
         <osVersionInfo>
           <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />
         </osVersionInfo>
       </dependentOS>
     </dependency>
   ```

3. Per un prerequisito per una determinata versione di Common Language Runtime, aggiungere l'attributo alla voce che `supportUrl` specifica la dipendenza di Common Language `dependentAssembly` Runtime:

   ```xml
     <dependency>
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">
         <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />
       </dependentAssembly>
     </dependency>
   ```

4. Per un prerequisito per un assembly che deve essere preinstallato nella Global Assembly Cache, impostare per `supportUrl` `dependentAssembly` l'elemento che specifica l'assembly richiesto:

   ```xml
     <dependency>
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">
         <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />
       </dependentAssembly>
     </dependency>
   ```

5. facoltativo. Per le applicazioni che hanno come destinazione .NET Framework 4, aprire il manifesto della distribuzione (file con estensione *application)* per l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] in un editor di testo.

6. Per un .NET Framework 4 prerequisito, aggiungere `supportUrl` l'attributo `compatibleFrameworks` all'elemento :

   ```xml
   <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">
     <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />
     <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />
   </compatibleFrameworks>
   ```

7. Dopo aver modificato manualmente il manifesto dell'applicazione, è necessario firmare nuovamente il manifesto dell'applicazione usando il certificato digitale, quindi aggiornare e firmare di nuovo anche il manifesto di distribuzione. Usare gli *Mage.exe* o *MageUI.exe* SDK per eseguire questa attività, poiché la rigenerazione di questi file usando cancella le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modifiche manuali. Per altre informazioni sull'Mage.exe per firmare nuovamente i manifesti, vedere Procedura: Firmare nuovamente manifesti di [applicazione e distribuzione.](../deployment/how-to-re-sign-application-and-deployment-manifests.md)

## <a name="net-framework-security"></a>.NET Framework (sicurezza)
 L'URL di supporto non viene visualizzato nella finestra di dialogo se l'applicazione è contrassegnata per l'esecuzione con attendibilità parziale.

## <a name="see-also"></a>Vedi anche
- [Mage.exe (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [Procedura dettagliata: Distribuire manualmente un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [\<compatibleFrameworks> Elemento](../deployment/compatibleframeworks-element-clickonce-deployment.md)
- [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md)
- [Prerequisiti per la distribuzione dell'applicazione](../deployment/application-deployment-prerequisites.md)