---
title: '&lt;&gt;elemento entryPoint (applicazione ClickOnce) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 615a606dc4d04682a9d5a1a69c91b4d2cd67de15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62928618"
---
# <a name="ltentrypointgt-element-clickonce-application"></a>&lt;&gt;elemento entryPoint (applicazione ClickOnce)
Identifica l'assembly che deve essere eseguito quando l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione viene eseguita su un computer client.

## <a name="syntax"></a>Sintassi

```xml
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
 L'elemento `entryPoint` è obbligatorio e si trova nello spazio dei nomi `urn:schemas-microsoft-com:asm.v2` . `entryPoint`In un manifesto dell'applicazione può essere definito un solo elemento.

 L'elemento `entryPoint` presenta l'attributo seguente:

|Attributo|Descrizione|
|---------------|-----------------|
|`name`|Facoltativa. Questo valore non viene utilizzato dal .NET Framework.|

 `entryPoint` presenta gli elementi seguenti:

## <a name="assemblyidentity"></a>assemblyIdentity
 Obbligatorio. Il ruolo di `assemblyIdentity` e i relativi attributi sono definiti nell' [ \<assemblyIdentity> elemento](../deployment/assemblyidentity-element-clickonce-application.md).

 L' `processorArchitecture` attributo di questo elemento e l' `processorArchitecture` attributo definito in `assemblyIdentity` un'altra posizione nel manifesto dell'applicazione devono corrispondere.

## <a name="commandline"></a>commandLine
 Obbligatorio. Deve essere un elemento figlio dell' `entryPoint` elemento. Non ha elementi figlio e ha gli attributi seguenti.

| Attributo | Descrizione |
|--------------| - |
| `file` | Obbligatorio. Riferimento locale all'assembly di avvio per l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione. Questo valore non può contenere separatori di percorso barra (/) o barra rovesciata ( \\ ). |
| `parameters` | Obbligatorio. Descrive l'azione da eseguire con il punto di ingresso. L'unico valore valido è `run` ; se viene fornita una stringa vuota, `run` si presuppone. |

## <a name="customhostrequired"></a>customHostRequired
 facoltativo. Se incluso, specifica che questa distribuzione contiene un componente che verrà distribuito all'interno di un host personalizzato e non è un'applicazione autonoma.

 Se questo elemento è presente, `assemblyIdentity` anche gli `commandLine` elementi e non devono essere presenti. In caso affermativo, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] genererà un errore di convalida durante l'installazione.

 Questo elemento non ha attributi e nessun elemento figlio.

## <a name="customux"></a>customUX
 facoltativo. Specifica che l'applicazione viene installata e gestita da un programma di installazione personalizzato e non crea una voce del menu Start, un collegamento o una voce di installazione applicazioni.

```xml
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />
```

 Un'applicazione che include l'elemento customUX deve fornire un programma di installazione personalizzato che usa la <xref:System.Deployment.Application.InPlaceHostingManager> classe per eseguire le operazioni di installazione. Non è possibile installare un'applicazione con questo elemento facendo doppio clic sul relativo manifesto o setup.exe programma di avvio automatico dei prerequisiti. Il programma di installazione personalizzato può creare voci di menu Start, scelte rapide e aggiungere o rimuovere le voci di programmi. Se il programma di installazione personalizzato non crea una voce Aggiungi o Rimuovi programmi, deve archiviare l'identificatore di sottoscrizione fornito dalla <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> proprietà e consentire all'utente di disinstallare l'applicazione in un secondo momento chiamando il <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A> metodo. Per ulteriori informazioni, vedere [procedura dettagliata: creazione di un programma di installazione personalizzato per un'applicazione ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md).

## <a name="remarks"></a>Osservazioni
 Questo elemento identifica l'assembly e il punto di ingresso per l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione.

 Non è possibile usare `commandLine` per passare parametri nell'applicazione in fase di esecuzione. È possibile accedere ai parametri della stringa di query per una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione dall'applicazione <xref:System.AppDomain> . Per altre informazioni, vedere [procedura: recuperare informazioni sulle stringhe di query in un'applicazione ClickOnce in linea](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato un `entryPoint` elemento in un manifesto dell'applicazione per un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione. Questo esempio di codice fa parte di un esempio più ampio fornito per l'argomento [manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md) .

```xml
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
- [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)
