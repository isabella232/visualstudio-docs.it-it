---
title: '&lt;&gt;elemento Deployment (distribuzione ClickOnce) | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194650"
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;&gt;elemento Deployment (distribuzione ClickOnce)
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
|`install`|Obbligatorio. Specifica se questa applicazione definisce una presenza nel menu **Start** di Windows e nell'applicazione **installazione** applicazioni del pannello di controllo. I valori validi sono `true` e `false`. Se `false` , eseguirà [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] sempre la versione più recente dell'applicazione dalla rete e non riconoscerà l' `subscription` elemento.|  
|`minimumRequiredVersion`|facoltativo. Specifica la versione minima dell'applicazione che può essere eseguita nel client. Se il numero di versione dell'applicazione è inferiore al numero di versione specificato nel manifesto di distribuzione, l'applicazione non verrà eseguita. I numeri di versione devono essere specificati nel formato `N.N.N.N` , dove `N` è un Unsigned Integer. Se l' `install` attributo è `false` , `minimumRequiredVersion` non deve essere impostato.|  
|`mapFileExtensions`|facoltativo. Il valore predefinito è `false`. Se `true` , tutti i file nella distribuzione devono disporre di un'estensione. deploy. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Questa estensione verrà eliminata da questi file non appena vengono scaricati dal server Web. Se si pubblica l'applicazione usando [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , questa estensione viene aggiunta automaticamente a tutti i file. Questo parametro consente di scaricare tutti i file all'interno di una [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] distribuzione da un server Web che blocca la trasmissione di file che terminano con estensioni "non sicure", ad esempio. exe.|  
|`disallowUrlActivation`|facoltativo. Il valore predefinito è `false`. Se `true` , impedisce l'avvio di un'applicazione installata facendo clic sull'URL o immettendo l'URL in Internet Explorer. Se l' `install` attributo non è presente, questo attributo viene ignorato.|  
|`trustURLParameters`|facoltativo. Il valore predefinito è `false`. Se `true` , consente all'URL di contenere i parametri della stringa di query passati nell'applicazione, in modo analogo agli argomenti della riga di comando che vengono passati a un'applicazione della riga di comando. Per altre informazioni, vedere [procedura: recuperare informazioni sulle stringhe di query in un'applicazione ClickOnce in linea](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).<br /><br /> Se l' `disallowUrlActivation` attributo è `true` , `trustUrlParameters` deve essere escluso dal manifesto o impostato in modo esplicito su `false` .|  
  
 L' `deployment` elemento contiene anche gli elementi figlio seguenti.  
  
## <a name="subscription"></a>sottoscrizione  
 facoltativo. Contiene l' `update` elemento. L'elemento `subscription` non ha attributi. Se l' `subscription` elemento non esiste, l' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione non analizzerà mai gli aggiornamenti. Se l' `install` attributo dell' `deployment` elemento è `false` , l' `subscription` elemento viene ignorato, perché un' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione avviata dalla rete usa sempre la versione più recente.  
  
## <a name="update"></a>update  
 Obbligatorio. Questo elemento è figlio dell' `subscription` elemento e contiene l' `beforeApplicationStartup` `expiration` elemento o. `beforeApplicationStartup` e `expiration` non possono essere specificati nello stesso manifesto di distribuzione.  
  
 L'elemento `update` non ha attributi.  
  
## <a name="beforeapplicationstartup"></a>beforeApplicationStartup  
 facoltativo. Questo elemento è figlio dell' `update` elemento e non ha attributi. Quando l' `beforeApplicationStartup` elemento esiste, l'applicazione viene bloccata quando [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Controlla la presenza di aggiornamenti, se il client è online. Se questo elemento non esiste, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] analizzerà prima di tutto gli aggiornamenti in base ai valori specificati per l' `expiration` elemento. `beforeApplicationStartup` e `expiration` non possono essere specificati nello stesso manifesto di distribuzione.  
  
## <a name="expiration"></a>expiration  
 facoltativo. Questo elemento è figlio dell' `update` elemento e non ha elementi figlio. `beforeApplicationStartup` e `expiration` non possono essere specificati nello stesso manifesto di distribuzione. Quando viene eseguito il controllo dell'aggiornamento e viene rilevata una versione aggiornata, la nuova versione viene memorizzata nella cache mentre viene eseguita la versione esistente. La nuova versione viene quindi installata al successivo avvio dell' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione.  
  
 L' `expiration` elemento supporta gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`maximumAge`|Obbligatorio. Identifica l'età dell'aggiornamento corrente prima che l'applicazione esegua una verifica degli aggiornamenti. L'unità di tempo è determinata dall' `unit` attributo.|  
|`unit`|Obbligatorio. Identifica l'unità di tempo per `maximumAge` . Le unità valide sono `hours` , `days` e `weeks` .|  
  
## <a name="deploymentprovider"></a>deploymentProvider  
 Per la .NET Framework 2,0, questo elemento è obbligatorio se il manifesto di distribuzione contiene una `subscription` sezione. Per la .NET Framework 3,5 e versioni successive, questo elemento è facoltativo e per impostazione predefinita viene utilizzato il percorso del server e del file in cui è stato individuato il manifesto di distribuzione.  
  
 Questo elemento è figlio dell'elemento `deployment` e ha l'attributo seguente.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`codebase`|Obbligatorio. Identifica il percorso, come Uniform Resource Identifier (URI), del manifesto di distribuzione usato per aggiornare l' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione. Questo elemento consente inoltre di inviare i percorsi di aggiornamento per le installazioni basate su CD. Deve essere un URI valido.|  
  
## <a name="remarks"></a>Osservazioni  
 È possibile configurare l' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applicazione in modo che analizzi la disponibilità di aggiornamenti all'avvio, analizzi gli aggiornamenti dopo l'avvio o non verifichi mai gli aggiornamenti. Per analizzare la disponibilità di aggiornamenti all'avvio, verificare che l' `beforeApplicationStartup` elemento esista nell' `update` elemento. Per cercare gli aggiornamenti dopo l'avvio, verificare che l' `expiration` elemento esista nell' `update` elemento e che siano stati specificati gli intervalli di aggiornamento.  
  
 Per disabilitare il controllo degli aggiornamenti, rimuovere l' `subscription` elemento. Quando si specifica nel manifesto di distribuzione per non analizzare mai gli aggiornamenti, è comunque possibile verificare manualmente la disponibilità di aggiornamenti tramite il <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> metodo.  
  
 Per ulteriori informazioni sul modo in cui deploymentProvider è correlato agli aggiornamenti, vedere [scelta di una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio di codice riportato di seguito viene illustrato un `deployment` elemento in un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesto di distribuzione. Nell'esempio viene usato un `deploymentProvider` elemento per indicare il percorso di aggiornamento preferito.  
  
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
