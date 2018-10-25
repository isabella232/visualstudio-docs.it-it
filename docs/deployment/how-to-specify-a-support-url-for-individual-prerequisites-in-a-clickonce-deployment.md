---
title: 'Procedura: specificare un URL di supporto per i singoli prerequisiti in una distribuzione ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1e93e8ab84a751c447488e1b4dc6e3e6779b86b8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913281"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Procedura: specificare un URL di supporto per i singoli prerequisiti in una distribuzione ClickOnce
Oggetto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] possibile testare la distribuzione per un numero di prerequisiti che devono essere disponibili nel computer client per il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] esecuzione dell'applicazione. Queste dipendenze includono la versione minima richiesta del [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], la versione del sistema operativo e tutti gli assembly che devono essere preinstallati nella global assembly cache (GAC). [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], tuttavia, non è possibile installare uno di questi prerequisiti stesso. Se un prerequisito non viene trovato, semplicemente arresta l'installazione e visualizza una finestra di dialogo che spiega il motivo per cui l'installazione non è riuscita.  
  
 Esistono due metodi per l'installazione dei prerequisiti. È possibile installarli usando un'applicazione di avvio automatico. In alternativa, è possibile specificare un URL di supporto per i singoli prerequisiti, viene visualizzato agli utenti nella finestra di dialogo se il prerequisito non viene trovato. La pagina fa riferimento tale URL può contenere collegamenti a istruzioni per installare i prerequisiti richiesti. Se un'applicazione non specifica un URL di supporto per un prerequisito per singoli [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] consente di visualizzare l'URL del supporto specificato nel manifesto di distribuzione per l'applicazione nel suo complesso, se è definito.  
  
 Sebbene [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], *Mage.exe*, e *MageUI.exe* può essere utilizzato per generare [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] le distribuzioni, nessuno di questi strumenti supportano direttamente specificando un URL di supporto per i singoli prerequisiti. Questo documento viene descritto come modificare la distribuzione manifesto dell'applicazione e distribuzione per includere questi URL di supporto.  
  
### <a name="specify-a-support-url-for-an-individual-prerequisite"></a>Specificare un URL di supporto per un singolo prerequisito  
  
1. Aprire il manifesto dell'applicazione (il *manifest* file) per il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione in un editor di testo.  
  
2. Per un prerequisito necessario per sistema operativo, aggiungere il `supportUrl` dell'attributo di `dependentOS` elemento:  
  
   ```xml  
    <dependency>  
       <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
         <osVersionInfo>  
           <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
         </osVersionInfo>  
       </dependentOS>  
     </dependency>  
   ```  
  
3. Per un prerequisito per una determinata versione di common language runtime, aggiungere il `supportUrl` dell'attributo di `dependentAssembly` voce che indica la dipendenza di common language runtime:  
  
   ```xml  
     <dependency>  
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
         <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
       </dependentAssembly>  
     </dependency>  
   ```  
  
4. Per un prerequisito per un assembly che deve essere preinstallato nella global assembly cache, impostare il `supportUrl` per il `dependentAssembly` elemento che specifica l'assembly richiesto:  
  
   ```xml  
     <dependency>  
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
         <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
       </dependentAssembly>  
     </dependency>  
   ```  
  
5. Facoltativo. Per le applicazioni destinate a .NET Framework 4, aprire il manifesto di distribuzione (il *Application* file) per il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione in un editor di testo.  
  
6. Per un prerequisito di .NET Framework 4, aggiungere il `supportUrl` dell'attributo di `compatibleFrameworks` elemento:  
  
   ```xml  
   <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
     <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
     <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
   </compatibleFrameworks>  
   ```  
  
7. Dopo aver modificato manualmente il manifesto dell'applicazione, è necessario firmare nuovamente il manifesto dell'applicazione utilizzando il certificato digitale, quindi aggiornare e firmare nuovamente il manifesto di distribuzione nonché. Usare la *Mage.exe* oppure *MageUI.exe* strumenti SDK per eseguire questa attività, come la rigenerazione di questi file tramite [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Cancella le modifiche manuali apportate. Per altre informazioni sull'uso di Mage.exe per firmare nuovamente i manifesti, vedere [procedura: re-sign Application and Deployment Manifests](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="net-framework-security"></a>.NET Framework (sicurezza)  
 L'URL del supporto non viene visualizzata nella finestra di dialogo se l'applicazione viene contrassegnata per essere eseguita in attendibilità parziale.  
  
## <a name="see-also"></a>Vedere anche  
 [Mage.exe (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [Procedura dettagliata: Distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks > elemento](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Prerequisiti per la distribuzione dell'applicazione](../deployment/application-deployment-prerequisites.md)