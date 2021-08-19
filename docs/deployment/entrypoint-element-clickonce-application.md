---
title: '&lt;Elemento entryPoint &gt; (ClickOnce Application) | Microsoft Docs'
description: L'elemento entryPoint identifica l'assembly che deve essere eseguito quando ClickOnce'applicazione viene eseguita in un computer client.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: a6268f2ff1c8d60184ddb290260fa33c841b1d51
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122146394"
---
# <a name="ltentrypointgt-element-clickonce-application"></a>&lt;Elemento entryPoint &gt; (ClickOnce applicazione)
Identifica l'assembly che deve essere eseguito quando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] l'applicazione viene eseguita in un computer client.

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
 L'elemento `entryPoint` è obbligatorio e si trova nello spazio dei nomi `urn:schemas-microsoft-com:asm.v2` . In un manifesto `entryPoint` dell'applicazione può essere definito un solo elemento.

 L'elemento `entryPoint` presenta l'attributo seguente:

|Attributo|Descrizione|
|---------------|-----------------|
|`name`|Facoltativa. Questo valore non viene usato da .NET Framework.|

 `entryPoint` presenta gli elementi seguenti:

## <a name="assemblyidentity"></a>assemblyIdentity
 Obbligatorio. Il ruolo di `assemblyIdentity` e i relativi attributi sono definiti nell'elemento . [ \<assemblyIdentity> ](../deployment/assemblyidentity-element-clickonce-application.md)

 L'attributo di questo elemento e l'attributo definito in altro punto nel `processorArchitecture` `processorArchitecture` manifesto `assemblyIdentity` dell'applicazione devono corrispondere.

## <a name="commandline"></a>commandLine
 Obbligatorio. Deve essere un elemento figlio `entryPoint` dell'elemento . Non ha elementi figlio e dispone degli attributi seguenti.

| Attributo | Descrizione |
|--------------| - |
| `file` | Obbligatorio. Riferimento locale all'assembly di avvio per [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] l'applicazione. Questo valore non può contenere separatori di percorso barra (/) o barra rovesciata ( \\ ). |
| `parameters` | Obbligatorio. Descrive l'azione da eseguire con il punto di ingresso. L'unico valore valido è . Se viene specificata `run` una stringa vuota, `run` viene presupposto. |

## <a name="customhostrequired"></a>customHostRequired
 facoltativo. Se incluso, specifica che questa distribuzione contiene un componente che verrà distribuito all'interno di un host personalizzato e non è un'applicazione autonoma.

 Se questo elemento è presente, `assemblyIdentity` gli elementi e non devono essere `commandLine` presenti. In caso contrario, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] genererà un errore di convalida durante l'installazione.

 Questo elemento non ha attributi e nessun elemento figlio.

## <a name="customux"></a>customUX
 facoltativo. Specifica che l'applicazione viene installata e gestita da un programma di installazione personalizzato e non crea una voce menu Start, un collegamento o una voce Installazione applicazioni.

```xml
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />
```

 Un'applicazione che include l'elemento customUX deve fornire un programma di installazione personalizzato che usa la <xref:System.Deployment.Application.InPlaceHostingManager> classe per eseguire operazioni di installazione. Un'applicazione con questo elemento non può essere installata facendo doppio clic sul manifesto o setup.exe bootstrap prerequisito. Il programma di installazione personalizzato può creare menu Start, i collegamenti e le voci Installazione applicazioni. Se il programma di installazione personalizzato non crea una voce Installazione applicazioni, deve archiviare l'identificatore di sottoscrizione fornito dalla proprietà e consentire all'utente di disinstallare l'applicazione in un secondo momento chiamando <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> il <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A> metodo . Per altre informazioni, vedere [Procedura dettagliata: Creazione di un programma di installazione personalizzato per un ClickOnce App.](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md)

## <a name="remarks"></a>Commenti
 Questo elemento identifica l'assembly e il punto di ingresso per [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] l'applicazione.

 Non è possibile `commandLine` usare per passare parametri all'applicazione in fase di esecuzione. È possibile accedere ai parametri della stringa di query per [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] una distribuzione da <xref:System.AppDomain> . Per altre informazioni, vedere Procedura: Recuperare informazioni sulla [stringa di query in un'applicazione ClickOnce online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).

## <a name="example"></a>Esempio
 L'esempio di codice seguente illustra un `entryPoint` elemento in un manifesto dell'applicazione per un'applicazione. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Questo esempio di codice fa parte di un esempio più esaustivo fornito per [l'ClickOnce manifesto dell'applicazione.](../deployment/clickonce-application-manifest.md)

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

## <a name="see-also"></a>Vedi anche
- [ClickOnce manifesto dell'applicazione](../deployment/clickonce-application-manifest.md)
