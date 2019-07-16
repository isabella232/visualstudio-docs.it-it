---
title: '&lt;punto di ingresso&gt; elemento (applicazione ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#commandLine
- urn:schemas-microsoft-com:asm.v2#entryPoint
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <entryPoint> element [ClickOnce application manifest]
- manifests [ClickOnce], entryPoint element
ms.assetid: 10ad3083-10c1-4189-a870-9bba2eab244f
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9ce9fcbddf54dff0ee8574d0c2a5a3df4d8b5c7e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68193500"
---
# <a name="ltentrypointgt-element-clickonce-application"></a>&lt;punto di ingresso&gt; elemento (applicazione ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifica l'assembly che deve essere eseguite quando questo [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione viene eseguita in un computer client.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      <entryPoint  
   name  
>  
   <assemblyIdentity  
      name  
      version  
      processorArchitecture  
      language  
   />  
   <commandLine  
      file  
      parameters  
   />  
   <customHostRequired />  
   <customUX />  
</entryPoint>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 L'elemento `entryPoint` è obbligatorio e si trova nello spazio dei nomi `urn:schemas-microsoft-com:asm.v2` . Potrebbe essere presente solo un `entryPoint` elemento definito in un manifesto dell'applicazione.  
  
 L'elemento `entryPoint` presenta l'attributo seguente:  
  
|Attributo|DESCRIZIONE|  
|---------------|-----------------|  
|`name`|facoltativo. Questo valore non viene utilizzato da .NET Framework.|  
  
 `entryPoint` presenta gli elementi seguenti:  
  
## <a name="assemblyidentity"></a>assemblyIdentity  
 Richiesto. Il ruolo del `assemblyIdentity` e relativi attributi sono definiti [ \<assemblyIdentity > elemento](../deployment/assemblyidentity-element-clickonce-application.md).  
  
 Il `processorArchitecture` attributo di questo elemento e il `processorArchitecture` attributo definito nella `assemblyIdentity` altrove nell'applicazione manifesto deve corrispondere.  
  
## <a name="commandline"></a>commandLine  
 Richiesto. Deve essere un figlio di `entryPoint` elemento. Non dispone di alcun elemento figlio e ha gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`file`|Richiesto. Un riferimento locale all'assembly di avvio per il [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dell'applicazione. Questo valore non può contenere barra (/) o una barra rovesciata (\\) separatori del percorso.|  
|`parameters`|Richiesto. Descrive l'azione da intraprendere con il punto di ingresso. È l'unico valore valido `run`; se viene fornita una stringa vuota, `run` presuppone.|  
  
## <a name="customhostrequired"></a>customHostRequired  
 facoltativo. Se incluso, specifica che la distribuzione contiene un componente che verrà distribuito all'interno di un host personalizzato e non è un'applicazione autonoma.  
  
 Se questo elemento è presente, il `assemblyIdentity` e `commandLine` elementi non possono essere presenti. In tal caso, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] genererà un errore di convalida durante l'installazione.  
  
 Questo elemento dispone di alcun attributo e nessun elemento figlio.  
  
## <a name="customux"></a>customUX  
 facoltativo. Specifica che l'applicazione è installata e gestito da un programma di installazione personalizzato e non creare una voce di menu Start, scelta rapida o Aggiungi o Rimuovi voce di programmi.  
  
```  
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />  
```  
  
 Un'applicazione che include l'elemento customUX deve fornire un programma di installazione personalizzato che usa il <xref:System.Deployment.Application.InPlaceHostingManager> classe per eseguire le operazioni di installazione. Un'applicazione con questo elemento non può essere installata facendo doppio clic sul relativo manifesto o setup.exe avvio automatico di prerequisiti. Il programma di installazione personalizzato è possibile creare le voci di menu Start, collegamenti e voci Aggiungi / Rimuovi programmi. Se il programma di installazione personalizzato non crea una voce in Installazione applicazioni, è necessario archiviare l'identificatore della sottoscrizione fornito per il <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> proprietà e consentono all'utente di disinstallare l'applicazione in un secondo momento chiamando il <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A> (metodo). Per altre informazioni, vedere [Procedura dettagliata: creazione di un programma di installazione personalizzato per un'applicazione ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md).  
  
## <a name="remarks"></a>Note  
 Questo elemento identifica l'assembly e punto di ingresso per il [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dell'applicazione.  
  
 Non è possibile usare `commandLine` passare parametri all'interno dell'applicazione in fase di esecuzione. È possibile accedere ai parametri della stringa di query per un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] distribuzione dell'applicazione <xref:System.AppDomain>. Per altre informazioni, vedere [Procedura: recuperare informazioni sulle stringhe di query in un'applicazione ClickOnce online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente illustra un' `entryPoint` elemento in un manifesto dell'applicazione per un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dell'applicazione. Questo esempio di codice è parte di un esempio più esaustivo disponibile per il [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md) argomento.  
  
```  
<!-- Identify the main code entrypoint. -->  
<!-- This code runs the main method in an executable assembly. -->  
  <entryPoint>  
    <assemblyIdentity   
      name="MyApplication"   
      version="1.0.0.0"  
      language="neutral"  
      processorArchitecture="x86" />  
    <commandLine file="MyApplication.exe" parameters="" />  
  </entryPoint>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)
