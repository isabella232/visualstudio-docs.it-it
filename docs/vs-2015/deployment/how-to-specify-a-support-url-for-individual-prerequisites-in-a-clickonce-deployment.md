---
title: 'Procedura: specificare un URL di supporto per i singoli prerequisiti in una distribuzione ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- ClickOnce deployment, URLs
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: bdd366cb8ac86f20e7457178f63aa553a0814158
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831575"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Procedura: specificare un URL di supporto per i singoli prerequisiti in una distribuzione ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Oggetto [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] possibile testare la distribuzione per un numero di prerequisiti che devono essere disponibili nel computer client per il [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] esecuzione dell'applicazione. Queste includono la versione minima richiesta del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], la versione del sistema operativo e tutti gli assembly che devono essere preinstallati nella global assembly cache (GAC). [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], tuttavia, non è possibile installare uno di questi prerequisiti stesso. Se un prerequisito non viene trovato, semplicemente arresta l'installazione e visualizza una finestra di dialogo che spiega il motivo per cui l'installazione non è riuscita.  
  
 Esistono due metodi per l'installazione dei prerequisiti. È possibile installarli usando un'applicazione di avvio automatico. In alternativa, è possibile specificare un URL di supporto per i singoli prerequisiti, viene visualizzato agli utenti nella finestra di dialogo se il prerequisito non viene trovato. La pagina fa riferimento tale URL può contenere collegamenti a istruzioni per installare i prerequisiti richiesti. Se un'applicazione non specifica un URL di supporto per un prerequisito per singoli [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] consente di visualizzare l'URL del supporto specificato nel manifesto di distribuzione per l'applicazione nel suo complesso, se è definito.  
  
 Sebbene [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], Mage.exe e MageUI.exe tutti utilizzabile per generare [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] le distribuzioni, nessuno di questi strumenti supportano direttamente specificando un URL di supporto per i singoli prerequisiti. Questo documento viene descritto come modificare la distribuzione manifesto dell'applicazione e distribuzione per includere questi URL di supporto.  
  
### <a name="specifying-a-support-url-for-an-individual-prerequisite"></a>Specificare un URL di supporto per un singolo prerequisito  
  
1.  Aprire il manifesto dell'applicazione (file. manifest) per il [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dell'applicazione in un editor di testo.  
  
2.  Per un prerequisito necessario per sistema operativo, aggiungere il `supportUrl` dell'attributo di `dependentOS` elemento:  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3.  Per un prerequisito per una determinata versione di common language runtime, aggiungere il `supportUrl` dell'attributo di `dependentAssembly` voce che indica la dipendenza di common language runtime:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4.  Per un prerequisito per un assembly che deve essere preinstallato nella global assembly cache, impostare il `supportUrl` per il `dependentAssembly` elemento che specifica l'assembly richiesto:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5.  Facoltativo. Per le applicazioni destinate a .NET Framework 4, aprire il manifesto di distribuzione (file con estensione Application) per il [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dell'applicazione in un editor di testo.  
  
6.  Per un prerequisito di .NET Framework 4, aggiungere il `supportUrl` dell'attributo di `compatibleFrameworks` elemento:  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7.  Dopo aver modificato manualmente il manifesto dell'applicazione, è necessario firmare nuovamente il manifesto dell'applicazione utilizzando il certificato digitale, quindi aggiornare e firmare nuovamente il manifesto di distribuzione nonché. È necessario usare Mage.exe o MageUI.exe SDK degli strumenti per portare a termine questa attività, come la rigenerazione di questi file tramite [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Cancella le modifiche manuali apportate. Per altre informazioni sull'uso di Mage.exe per firmare nuovamente i manifesti, vedere [procedura: re-sign Application and Deployment Manifests](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="net-framework-security"></a>Sicurezza di .NET Framework  
 L'URL del supporto non viene visualizzata nella finestra di dialogo se l'applicazione viene contrassegnata per essere eseguita in attendibilità parziale.  
  
## <a name="see-also"></a>Vedere anche  
 [Mage.exe (Strumento per la generazione e la modifica di manifesti)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [Procedura dettagliata: Distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks > elemento](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Prerequisiti per la distribuzione dell'applicazione](../deployment/application-deployment-prerequisites.md)



