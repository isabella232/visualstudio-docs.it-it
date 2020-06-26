---
title: URL di supporto per i prerequisiti nella distribuzione ClickOnce
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf474e4926403a9475860bfdc620ee4a6860f8aa
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "85381730"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Procedura: Specificare un URL di supporto per i singoli prerequisiti in una distribuzione ClickOnce
Una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione può verificare la presenza di alcuni prerequisiti che devono essere disponibili nel computer client per l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] esecuzione dell'applicazione. Queste dipendenze includono la versione minima richiesta del .NET Framework, la versione del sistema operativo e tutti gli assembly che devono essere preinstallati nella Global Assembly Cache (GAC). [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Tuttavia, non è in grado di installare alcuno di questi prerequisiti. Se un prerequisito non viene trovato, viene semplicemente interrotto l'installazione e viene visualizzata una finestra di dialogo che spiega il motivo per cui l'installazione non è riuscita.

 Sono disponibili due metodi per l'installazione dei prerequisiti. È possibile installarli usando un'applicazione del programma di avvio automatico. In alternativa, è possibile specificare un URL di supporto per i singoli prerequisiti, che viene visualizzato agli utenti nella finestra di dialogo se il prerequisito non viene trovato. La pagina a cui fa riferimento tale URL può contenere collegamenti alle istruzioni per l'installazione del prerequisito necessario. Se un'applicazione non specifica un URL di supporto per un singolo prerequisito, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Visualizza l'URL di supporto specificato nel manifesto di distribuzione per l'applicazione nel suo complesso, se definito.

 Sebbene [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sia possibile usare, *Mage.exe*e *MageUI.exe* per generare le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzioni, nessuno di questi strumenti supporta direttamente la specifica di un URL di supporto per i singoli prerequisiti. Questo documento descrive come modificare il manifesto dell'applicazione e la distribuzione del manifesto di distribuzione in modo da includere questi URL di supporto.

### <a name="specify-a-support-url-for-an-individual-prerequisite"></a>Specificare un URL di supporto per un singolo prerequisito

1. Aprire il manifesto dell'applicazione, ovvero il file con *estensione manifest* , per l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione in un editor di testo.

2. Per un prerequisito del sistema operativo, aggiungere l' `supportUrl` attributo all' `dependentOS` elemento:

   ```xml
    <dependency>
       <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">
         <osVersionInfo>
           <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />
         </osVersionInfo>
       </dependentOS>
     </dependency>
   ```

3. Per un prerequisito per una determinata versione del Common Language Runtime, aggiungere l' `supportUrl` attributo alla `dependentAssembly` voce che specifica la dipendenza Common Language Runtime:

   ```xml
     <dependency>
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">
         <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />
       </dependentAssembly>
     </dependency>
   ```

4. Per un prerequisito per un assembly che deve essere preinstallato nella Global Assembly Cache, impostare `supportUrl` per l' `dependentAssembly` elemento che specifica l'assembly richiesto:

   ```xml
     <dependency>
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">
         <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />
       </dependentAssembly>
     </dependency>
   ```

5. Facoltativa. Per le applicazioni destinate a .NET Framework 4, aprire il manifesto di distribuzione (il file dell' *applicazione* ) per l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione in un editor di testo.

6. Per un prerequisito di .NET Framework 4, aggiungere l' `supportUrl` attributo all' `compatibleFrameworks` elemento:

   ```xml
   <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">
     <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />
     <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />
   </compatibleFrameworks>
   ```

7. Dopo aver modificato manualmente il manifesto dell'applicazione, è necessario firmare di nuovo il manifesto dell'applicazione usando il certificato digitale, quindi aggiornare e firmare nuovamente il manifesto della distribuzione. Usare gli strumenti di *Mage.exe* o *MageUI.exe* SDK per completare questa attività, perché la rigenerazione di questi file con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Cancella le modifiche manuali. Per altre informazioni sull'uso di Mage.exe per ripetere la firma dei manifesti, vedere [procedura: ripetere la firma dei manifesti dell'applicazione e della distribuzione](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="net-framework-security"></a>.NET Framework (sicurezza)
 L'URL di supporto non viene visualizzato nella finestra di dialogo se l'applicazione è contrassegnata per l'esecuzione con attendibilità parziale.

## <a name="see-also"></a>Vedi anche
- [Mage.exe (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [Procedura dettagliata: Distribuire manualmente un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [\<compatibleFrameworks>elemento](../deployment/compatibleframeworks-element-clickonce-deployment.md)
- [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md)
- [Prerequisiti per la distribuzione dell'applicazione](../deployment/application-deployment-prerequisites.md)