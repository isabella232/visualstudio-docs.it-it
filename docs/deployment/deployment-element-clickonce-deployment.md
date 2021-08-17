---
title: '&lt;Elemento deployment &gt; (ClickOnce Deployment) | Microsoft Docs'
description: L'elemento deployment identifica gli attributi usati per la distribuzione degli aggiornamenti e l'esposizione al sistema.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 3067a5267c7bb4347b84aee55a1fdc47c5bfeb62
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090018"
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;elemento &gt; deployment (ClickOnce distribuzione)
Identifica gli attributi usati per la distribuzione degli aggiornamenti e l'esposizione al sistema.

## <a name="syntax"></a>Sintassi

```xml

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
 L'elemento `deployment` è obbligatorio e si trova nello spazio dei nomi `urn:schemas-microsoft-com:asm.v2` . L'elemento presenta gli attributi seguenti.

| Attributo | Descrizione |
|--------------------------| - |
| `install` | Obbligatorio. Specifica se questa applicazione definisce una presenza nel menu **Start** Windows e nell'applicazione Pannello di controllo Installazione **applicazioni.** I valori validi sono `true` e `false`. Se `false` , [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] eseguirà sempre la versione più recente dell'applicazione dalla rete e non riconoscerà l'elemento `subscription` . |
| `minimumRequiredVersion` | facoltativo. Specifica la versione minima dell'applicazione che può essere eseguita nel client. Se il numero di versione dell'applicazione è minore del numero di versione fornito nel manifesto della distribuzione, l'applicazione non verrà eseguita. I numeri di versione devono essere specificati nel formato `N.N.N.N` , dove è un intero senza `N` segno. Se `install` l'attributo è `false` , non deve essere `minimumRequiredVersion` impostato. |
| `mapFileExtensions` | facoltativo. Il valore predefinito è `false`. Se `true` , tutti i file nella distribuzione devono avere un'estensione .deploy. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] rimuoverà questa estensione da questi file non appena li scarica dal server Web. Se si pubblica l'applicazione usando , questa estensione viene [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aggiunta automaticamente a tutti i file. Questo parametro consente di scaricare tutti i file all'interno di una distribuzione da un server Web che blocca la trasmissione di file che [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] terminano con estensioni "non sicure", ad esempio .exe. |
| `disallowUrlActivation` | facoltativo. Il valore predefinito è `false`. Se `true` , impedisce l'avvio di un'applicazione installata facendo clic sull'URL o immettendo l'URL in Internet Explorer. Se `install` l'attributo non è presente, questo attributo viene ignorato. |
| `trustURLParameters` | facoltativo. Il valore predefinito è `false`. Se , consente all'URL di contenere parametri della stringa di query passati all'applicazione, analogamente agli argomenti della riga di comando vengono passati `true` a un'applicazione della riga di comando. Per altre informazioni, vedere Procedura: Recuperare informazioni sulla [stringa di query in un'applicazione ClickOnce online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).<br /><br /> Se `disallowUrlActivation` l'attributo è `true` , `trustUrlParameters` deve essere escluso dal manifesto o impostato in modo esplicito su `false` . |

 `deployment`L'elemento contiene anche gli elementi figlio seguenti.

## <a name="subscription"></a>sottoscrizione
 facoltativo. Contiene `update` l'elemento . L'elemento `subscription` non ha attributi. Se `subscription` l'elemento non esiste, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] l'applicazione non eseguirà mai l'analisi degli aggiornamenti. Se `install` l'attributo dell'elemento è , l'elemento viene ignorato, perché un'applicazione avviata dalla rete usa `deployment` sempre la versione più `false` `subscription` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] recente.

## <a name="update"></a>update
 Obbligatorio. Questo elemento è un elemento figlio `subscription` dell'elemento e contiene `beforeApplicationStartup` l'elemento o `expiration` . `beforeApplicationStartup` e `expiration` non possono essere specificati entrambi nello stesso manifesto di distribuzione.

 L'elemento `update` non ha attributi.

## <a name="beforeapplicationstartup"></a>beforeApplicationStartup
 facoltativo. Questo elemento è un elemento figlio `update` dell'elemento e non dispone di attributi. Quando `beforeApplicationStartup` l'elemento esiste, l'applicazione verrà bloccata quando verifica la disponibilità di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aggiornamenti, se il client è online. Se questo elemento non esiste, cerca prima di tutto gli [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aggiornamenti in base ai valori specificati per l'elemento. `expiration` `beforeApplicationStartup` e `expiration` non possono essere specificati entrambi nello stesso manifesto di distribuzione.

## <a name="expiration"></a>expiration
 facoltativo. Questo elemento è un elemento figlio `update` dell'elemento e non ha elementi figlio. `beforeApplicationStartup` e `expiration` non possono essere specificati entrambi nello stesso manifesto di distribuzione. Quando viene eseguito il controllo degli aggiornamenti e viene rilevata una versione aggiornata, la nuova versione viene memorizzata nella cache durante l'esecuzione della versione esistente. La nuova versione viene quindi installata al successivo avvio [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione.

 `expiration`L'elemento supporta gli attributi seguenti.

|Attributo|Descrizione|
|---------------|-----------------|
|`maximumAge`|Obbligatorio. Identifica l'età dell'aggiornamento corrente prima che l'applicazione esegua un controllo di aggiornamento. L'unità di tempo è determinata `unit` dall'attributo .|
|`unit`|Obbligatorio. Identifica l'unità di tempo per `maximumAge` . Le unità valide `hours` sono `days` , e `weeks` .|

## <a name="deploymentprovider"></a>deploymentProvider
 Per la .NET Framework 2.0, questo elemento è obbligatorio se il manifesto della distribuzione contiene una `subscription` sezione. Per il .NET Framework 3.5 e versioni successive, questo elemento è facoltativo e per impostazione predefinita verrà utilizzato il server e il percorso del file in cui è stato individuato il manifesto di distribuzione.

 Questo elemento è figlio dell'elemento `deployment` e ha l'attributo seguente.

| Attributo | Descrizione |
|------------| - |
| `codebase` | Obbligatorio. Identifica il percorso, come Uniform Resource Identifier (URI), del manifesto della distribuzione utilizzato per aggiornare [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] l'applicazione. Questo elemento consente anche di inoltrare i percorsi di aggiornamento per le installazioni basate su CD. Deve essere un URI valido. |

## <a name="remarks"></a>Commenti
 È possibile configurare [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] l'applicazione in modo da cercare gli aggiornamenti all'avvio, cercare gli aggiornamenti dopo l'avvio o non verificare mai la presenza di aggiornamenti. Per cercare gli aggiornamenti all'avvio, assicurarsi che `beforeApplicationStartup` l'elemento esista sotto `update` l'elemento . Per cercare gli aggiornamenti dopo l'avvio, assicurarsi che l'elemento esista nell'elemento e che siano specificati `expiration` `update` gli intervalli di aggiornamento.

 Per disabilitare il controllo degli aggiornamenti, rimuovere `subscription` l'elemento . Quando si specifica nel manifesto della distribuzione di non eseguire mai l'analisi degli aggiornamenti, è comunque possibile controllare manualmente la presenza di aggiornamenti usando il <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> metodo .

 Per altre informazioni sulla relazione tra deploymentProvider e gli aggiornamenti, vedere [Choosing a ClickOnce Update Strategy](../deployment/choosing-a-clickonce-update-strategy.md).

## <a name="examples"></a>Esempio
 Nell'esempio di codice seguente viene illustrato un `deployment` elemento in un manifesto di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione. Nell'esempio viene utilizzato `deploymentProvider` un elemento per indicare il percorso di aggiornamento preferito.

```xml
<deployment install="true" minimumRequiredVersion="2.0.0.0" mapFileExtension="true" trustUrlParameters="true">
    <subscription>
      <update>
        <expiration maximumAge="6" unit="hours" />
      </update>
    </subscription>
    <deploymentProvider codebase="http://www.adatum.com/MyApplication.application" />
  </deployment>
```

## <a name="see-also"></a>Vedi anche
- [ClickOnce manifesto della distribuzione](../deployment/clickonce-deployment-manifest.md)