---
title: Recuperare informazioni sulla stringa di query nell'app ClickOnce online
description: Informazioni su come un'ClickOnce può leggere la parte di query di un URL e su come usare MageUI per configurare l'applicazione in modo che accetti i parametri della stringa di query.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, query strings
- query strings, retrieving information
ms.assetid: 48ce098a-a075-481b-a5f5-c8ba11f63120
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 13a3a02b8853ede34ec257c01c0300e22fba136a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635267"
---
# <a name="how-to-retrieve-query-string-information-in-an-online-clickonce-application"></a>Procedura: Recuperare informazioni sulle stringhe di query in un'applicazione ClickOnce online
La *stringa di query* è la parte di un URL che inizia con un punto interrogativo (?) e contiene informazioni arbitrarie nel formato *nome = valore*. Si supponga di avere un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] denominata `WindowsApp1` che è ospitare in `servername`e di voler passare un valore per la variabile `username` quando l'applicazione viene avviata. L'aspetto dell'URL potrebbe essere simile al seguente:

 `http://servername/WindowsApp1.application?username=joeuser`

 Le due procedure seguenti illustrano come usare un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] per ottenere informazioni sulla stringa di query.

> [!NOTE]
> È possibile passare informazioni in una stringa di query solo quando l'applicazione viene avviata usando HTTP anziché una condivisione file o il file system locale.

 La prima procedura mostra come l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] può usare una piccola parte di codice per leggere questi valori quando l'applicazione viene avviata.

 La procedura seguente illustra come configurare l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] usando MageUI.exe in modo che possa accettare parametri della stringa di query. È necessario eseguire questa operazione ogni volta che si pubblica l'applicazione.

> [!NOTE]
> Prima di decidere se attivare questa funzionalità, vedere la sezione "Sicurezza" più avanti in questo argomento.

 Per informazioni su come creare una distribuzione usandoMage.exeoMageUI.exe, vedere Procedura dettagliata: Distribuire manualmente [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] un'applicazione ClickOnce distribuzione [.](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)  **

> [!NOTE]
> A partire da .NET Framework 3.5 SP1, è possibile passare argomenti della riga di comando in un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] offline. Se si desidera fornire argomenti all'applicazione, è possibile passare parametri al file di collegamento con l'estensione .APPREF-MS.

### <a name="to-obtain-query-string-information-from-a-clickonce-application"></a>Per ottenere informazioni sulla stringa di query da un'applicazione ClickOnce

1. Includere il codice seguente nel progetto. Per il funzionamento di questo codice, è necessario avere un riferimento a System.Web e aggiungere direttive o per `using` `Imports` System.Web, System.Collections.Specialized e System.Deployment.Application.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceQueryString/CS/Form1.cs" id="Snippet1":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceQueryString/VB/Form1.vb" id="Snippet1":::


2. Chiamare la funzione definita in precedenza per recuperare un <xref:System.Collections.DictionaryBase.Dictionary%2A> dei parametri della stringa di query, indicizzati per nome.

### <a name="to-enable-query-string-passing-in-a-clickonce-application-with-mageuiexe"></a>Per abilitare la stringa di query passando un'applicazione ClickOnce con MageUI.exe

1. Aprire il prompt dei comandi .NET e digitare:

   ```cmd
   MageUI
   ```

2. Nel menu **File** selezionare **Apri** e aprire il manifesto di distribuzione per l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , che è il file con l'estensione `.application` .

3. Selezionare il riquadro **Opzioni di distribuzione** nella finestra di navigazione a sinistra e selezionare la casella di controllo **Consenti passaggio di parametri URL all'applicazione** .

4. Nel menu **File** selezionare **Salva**.

> [!NOTE]
> In alternativa è possibile abilitare la stringa di query passando [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Selezionare la casella di controllo **Consenti passaggio di parametri URL all'applicazione** , a cui si accede aprendo **Proprietà progetto** selezionando la scheda **Pubblica** e facendo clic sul pulsante **Opzioni** e quindi selezionando **Manifesti**.

## <a name="robust-programming"></a>Programmazione efficiente
 Quando si usano parametri di stringa di query, è necessario valutare attentamente come l'applicazione è installata e attivata. Se l'applicazione è configurata per essere installata nel computer dell'utente dal Web o da una condivisione di rete, è probabile che l'utente attiverà l'applicazione solo una volta tramite l'URL. Successivamente, l'utente attiverà l'applicazione usando il collegamento nel menu **Start** . Di conseguenza, è garantito che l'applicazione riceverà gli argomenti della stringa di query una sola volta durante tutta la sua vita. Se si sceglie di archiviare questi argomenti sul computer dell'utente per uso futuro, è necessario archiviarli in modo sicuro e protetto.

 Se l'applicazione è solo online, verrà sempre attivata tramite un URL. Anche in questo caso, tuttavia, l'applicazione deve essere scritta in modo da funzionare correttamente se i parametri della stringa di query mancano o sono danneggiati.

## <a name="net-framework-security"></a>.NET Framework (sicurezza)
 Consentire il passaggio di parametri URL all'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] solo se si prevede di ripulire l'input da eventuali caratteri dannosi prima di usarlo. Una stringa incorporata con virgolette, barre o punto e virgola, ad esempio, potrebbe eseguire le operazioni di dati arbitrarie se viene impiegata senza essere filtrata in una query SQL su un database. Per altre informazioni sulla sicurezza delle stringhe di query, vedere [Panoramica degli exploit di script](/previous-versions/w1sw53ds(v=vs.140)).

## <a name="see-also"></a>Vedi anche
- [Proteggere le applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)