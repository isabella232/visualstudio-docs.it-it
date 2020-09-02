---
title: 'Procedura: specificare un URL di supporto per i singoli prerequisiti in una distribuzione ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1907b619bcc616c73d9b9e37af30722c02bf100e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65679962"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Procedura: specificare un URL di supporto per i singoli prerequisiti in una distribuzione ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] distribuzione può verificare la presenza di alcuni prerequisiti che devono essere disponibili nel computer client per l' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] esecuzione dell'applicazione. Sono incluse la versione minima richiesta di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , la versione del sistema operativo e tutti gli assembly che devono essere preinstallati nella global assembly cache (GAC). [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Tuttavia, non è in grado di installare alcuno di questi prerequisiti. Se un prerequisito non viene trovato, viene semplicemente interrotto l'installazione e viene visualizzata una finestra di dialogo che spiega il motivo per cui l'installazione non è riuscita.  
  
 Sono disponibili due metodi per l'installazione dei prerequisiti. È possibile installarli usando un'applicazione del programma di avvio automatico. In alternativa, è possibile specificare un URL di supporto per i singoli prerequisiti, che viene visualizzato agli utenti nella finestra di dialogo se il prerequisito non viene trovato. La pagina a cui fa riferimento tale URL può contenere collegamenti alle istruzioni per l'installazione del prerequisito necessario. Se un'applicazione non specifica un URL di supporto per un singolo prerequisito, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Visualizza l'URL di supporto specificato nel manifesto di distribuzione per l'applicazione nel suo complesso, se definito.  
  
 Sebbene [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sia possibile usare, Mage.exe e MageUI.exe per generare le [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] distribuzioni, nessuno di questi strumenti supporta direttamente la specifica di un URL di supporto per i singoli prerequisiti. Questo documento descrive come modificare il manifesto dell'applicazione e la distribuzione del manifesto di distribuzione in modo da includere questi URL di supporto.  
  
### <a name="specifying-a-support-url-for-an-individual-prerequisite"></a>Specifica di un URL di supporto per un singolo prerequisito  
  
1. Aprire il manifesto dell'applicazione, ovvero il file con estensione manifest, per l' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione in un editor di testo.  
  
2. Per un prerequisito del sistema operativo, aggiungere l' `supportUrl` attributo all' `dependentOS` elemento:  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3. Per un prerequisito per una determinata versione del Common Language Runtime, aggiungere l' `supportUrl` attributo alla `dependentAssembly` voce che specifica la dipendenza Common Language Runtime:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4. Per un prerequisito per un assembly che deve essere preinstallato nella Global Assembly Cache, impostare `supportUrl` per l' `dependentAssembly` elemento che specifica l'assembly richiesto:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5. facoltativo. Per le applicazioni destinate a .NET Framework 4, aprire il manifesto di distribuzione (il file dell'applicazione) per l' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione in un editor di testo.  
  
6. Per un prerequisito di .NET Framework 4, aggiungere l' `supportUrl` attributo all' `compatibleFrameworks` elemento:  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7. Dopo aver modificato manualmente il manifesto dell'applicazione, è necessario firmare di nuovo il manifesto dell'applicazione usando il certificato digitale, quindi aggiornare e firmare nuovamente il manifesto della distribuzione. Per eseguire questa attività, è necessario usare gli strumenti Mage.exe o MageUI.exe SDK, perché la rigenerazione di questi file con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Cancella le modifiche manuali. Per altre informazioni sull'uso di Mage.exe per ripetere la firma dei manifesti, vedere [procedura: ripetere la firma dei manifesti dell'applicazione e della distribuzione](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="net-framework-security"></a>Sicurezza di .NET Framework  
 L'URL di supporto non viene visualizzato nella finestra di dialogo se l'applicazione è contrassegnata per l'esecuzione con attendibilità parziale.  
  
## <a name="see-also"></a>Vedere anche  
 [Mage.exe (Strumento per la generazione e la modifica di manifesti)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [Procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks> Elemento](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Prerequisiti per la distribuzione dell'applicazione](../deployment/application-deployment-prerequisites.md)
