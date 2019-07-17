---
title: '&lt;distribuzione&gt; elemento (distribuzione ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#subscription
- urn:schemas-microsoft-com:asm.v2#beforeApplicationStartup
- urn:schemas-microsoft-com:asm.v2#deploymentProvider
- urn:schemas-microsoft-com:asm.v2#update
- urn:schemas-microsoft-com:asm.v2#deployment
- urn:schemas-microsoft-com:asm.v2#expiration
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <deployment> element [ClickOnce deployment manifest]
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a55b5519d5abb7b40aeca23fed1bc2f8ea2cc33d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194650"
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;distribuzione&gt; elemento (distribuzione ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifica gli attributi usati per la distribuzione degli aggiornamenti e l'esposizione al sistema.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      <deployment   
   install  
   minimumRequiredVersion  
   mapFileExtensions  
   disallowUrlActivation  
   trustUrlParameters  
>   
   <subscription>   
         <update>   
            <beforeApplicationStartup/>   
            <expiration  
               maximumAge  
               unit  
            />  
         </update>    
   </subscription>   
   <deploymentProvider   
      codebase   
   />   
</deployment>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 L'elemento `deployment` è obbligatorio e si trova nello spazio dei nomi `urn:schemas-microsoft-com:asm.v1` . L'elemento presenta gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`install`|Richiesto. Specifica se l'applicazione definisce una presenza in di Windows **avviare** dal menu e nel Pannello di controllo **Aggiungi / Rimuovi programmi** dell'applicazione. I valori validi sono `true` e `false`. Se `false`, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] eseguirà sempre la versione più recente di questa applicazione dalla rete e non riconoscerà il `subscription` elemento.|  
|`minimumRequiredVersion`|facoltativo. Specifica la versione minima dell'applicazione che è possibile eseguire sul client. Se il numero di versione dell'applicazione è inferiore al numero di versione specificato nel manifesto di distribuzione, l'applicazione non verrà eseguita. I numeri di versione devono essere specificati nel formato `N.N.N.N`, dove `N` è un intero senza segno. Se il `install` attributo è `false`, `minimumRequiredVersion` non deve essere impostato.|  
|`mapFileExtensions`|facoltativo. Il valore predefinito è `false`. Se `true`, tutti i file nella distribuzione devono avere l'estensione. deploy. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] rimuoverà questa estensione questi file, non appena li scarica dal server Web. Se si pubblica l'applicazione usando [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], questa estensione aggiunta automaticamente a tutti i file. Questo parametro consente di tutti i file all'interno di un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] distribuzione per essere scaricato da un server Web che impedisce la trasmissione dei file che terminano con "unsafe" estensioni, ad esempio .exe.|  
|`disallowUrlActivation`|facoltativo. Il valore predefinito è `false`. Se `true`, impedisce a un'applicazione installata in corso l'avvio facendo clic sull'URL o immettendo l'URL in Internet Explorer. Se il `install` attributo non è presente, questo attributo viene ignorato.|  
|`trustURLParameters`|facoltativo. Il valore predefinito è `false`. Se `true`, l'URL può contenere parametri di stringa di query che vengono passati all'applicazione, molto come argomenti della riga di comando vengono passati a un'applicazione della riga di comando. Per altre informazioni, vedere [Procedura: recuperare informazioni sulle stringhe di query in un'applicazione ClickOnce online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).<br /><br /> Se il `disallowUrlActivation` attributo è `true`, `trustUrlParameters` deve essere escluso dal manifesto o impostata esplicitamente su `false`.|  
  
 Il `deployment` elemento contiene anche i seguenti elementi figlio.  
  
## <a name="subscription"></a>sottoscrizione  
 facoltativo. Contiene il `update` elemento. L'elemento `subscription` non ha attributi. Se il `subscription` elemento non esiste, il [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione mai analizzi gli aggiornamenti. Se il `install` attributo del `deployment` elemento viene `false`, il `subscription` elemento viene ignorato, poiché un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione che viene sempre avviato dalla rete utilizza la versione più recente.  
  
## <a name="update"></a>update  
 Richiesto. Questo elemento è figlio del `subscription` elemento e può essere il `beforeApplicationStartup` o il `expiration` elemento. `beforeApplicationStartup` e `expiration` non possono essere specificati nel manifesto di distribuzione stesso.  
  
 L'elemento `update` non ha attributi.  
  
## <a name="beforeapplicationstartup"></a>beforeApplicationStartup  
 facoltativo. Questo elemento è figlio di `update` elemento e non include attributi. Quando la `beforeApplicationStartup` elemento esiste, l'applicazione sarà bloccato al momento [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Cerca aggiornamenti, se il client è online. Se questo elemento non esiste, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] analizzi prima di tutto gli aggiornamenti in base ai valori specificati per il `expiration` elemento. `beforeApplicationStartup` e `expiration` non possono essere specificati nel manifesto di distribuzione stesso.  
  
## <a name="expiration"></a>scadenza  
 facoltativo. Questo elemento è figlio di `update` elemento, e non ha elementi figlio. `beforeApplicationStartup` e `expiration` non possono essere specificati nel manifesto di distribuzione stesso. Quando si verifica la disponibilità di aggiornamenti e viene rilevata una versione aggiornata, la nuova versione vengono memorizzati nella cache mentre è in esecuzione la versione esistente. Installa quindi la nuova versione al successivo avvio del [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dell'applicazione.  
  
 Il `expiration` elemento supporta gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`maximumAge`|Richiesto. Identifica la modalità precedente dovrebbe diventare l'aggiornamento corrente prima che l'applicazione esegue una verifica dell'aggiornamento. L'unità di tempo è determinata dal `unit` attributo.|  
|`unit`|Richiesto. Identifica l'unità di tempo per `maximumAge`. Le unità valide sono `hours`, `days`, e `weeks`.|  
  
## <a name="deploymentprovider"></a>deploymentProvider  
 Per .NET Framework 2.0, questo elemento è obbligatorio se il manifesto di distribuzione contiene un `subscription` sezione. Per .NET Framework 3.5 e versioni successive, questo elemento è facoltativo e utilizzerà il server e il percorso di file in cui è stato individuato il manifesto di distribuzione.  
  
 Questo elemento è figlio dell'elemento `deployment` e ha l'attributo seguente.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`codebase`|Richiesto. Identifica la posizione del manifesto di distribuzione che viene usato per aggiornare, come Uniform Resource Identifier (URI), il [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dell'applicazione. Questo elemento consente inoltre di percorsi di aggiornamento per le installazioni basate sul CD di inoltro. Deve essere un URI valido.|  
  
## <a name="remarks"></a>Note  
 È possibile configurare il [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione cercare gli aggiornamenti all'avvio, cercare gli aggiornamenti dopo l'avvio o non controllare mai gli aggiornamenti. Per analizzare gli aggiornamenti all'avvio, assicurarsi che il `beforeApplicationStartup` elemento esiste sotto il `update` elemento. Per cercare gli aggiornamenti dopo l'avvio, assicurarsi che il `expiration` elemento esiste nel `update` elemento e che siano stati specificati gli intervalli di aggiornamento.  
  
 Per disabilitare il controllo degli aggiornamenti, rimuovere il `subscription` elemento. Quando si specifica nel manifesto di distribuzione mai cercare gli aggiornamenti, è possibile comunque manualmente cercare gli aggiornamenti usando il <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> (metodo).  
  
 Per altre informazioni sugli aggiornamenti di deploymentProvider, vedere [scelta di una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## <a name="examples"></a>Esempi  
 L'esempio di codice seguente illustra un `deployment` elemento in un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesto della distribuzione. Nell'esempio viene usato un `deploymentProvider` elemento per indicare il percorso di aggiornamento Preferiti.  
  
```  
<deployment install="true" minimumRequiredVersion="2.0.0.0" mapFileExtension="true" trustUrlParameters="true">  
    <subscription>  
      <update>  
        <expiration maximumAge="6" unit="hours" />  
      </update>  
    </subscription>  
    <deploymentProvider codebase="http://www.adatum.com/MyApplication.application" />  
  </deployment>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Manifesto di distribuzione ClickOnce](../deployment/clickonce-deployment-manifest.md)
