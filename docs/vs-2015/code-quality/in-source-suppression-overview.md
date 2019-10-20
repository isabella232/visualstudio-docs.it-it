---
title: Panoramica dell'eliminazione dell'origine | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: 42
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 63d405b0e62735c0c1e3d7bb716ea2db29bc19fe
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651566"
---
# <a name="in-source-suppression-overview"></a>Panoramica dell'eliminazione nell'origine
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'eliminazione nell'origine è la possibilità di escludere o ignorare le violazioni dell'analisi codice nel codice gestito aggiungendo l'attributo **SuppressMessage** ai segmenti di codice che causano le violazioni. L'attributo **SuppressMessage** è un attributo condizionale incluso nei metadati il dell'assembly del codice gestito solo se il simbolo di compilazione CODE_ANALYSIS è definito in fase di compilazione.

 In C++/CLI, utilizzare le macro CA_SUPPRESS_MESSAGE o CA_GLOBAL_SUPPRESS_MESSAGE nel file di intestazione per aggiungere l'attributo.

 Non usare le eliminazioni in origine nelle build di rilascio per evitare la spedizione accidentale dei metadati di eliminazione nel codice sorgente. A causa del costo di elaborazione dell'eliminazione nell'origine, le prestazioni dell'applicazione possono anche essere ridotte includendo i metadati di eliminazione nell'origine.

> [!NOTE]
> Non è necessario eseguire manualmente il codice di questi attributi. Per altre informazioni, vedere [procedura: non visualizzare avvisi tramite la voce di menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md). La voce di menu non è disponibile C++ per il codice.

## <a name="suppressmessage-attribute"></a>Attributo SuppressMessage
 Quando si fa clic con il pulsante destro del mouse su un avviso di analisi del codice nel **Elenco errori** e quindi si fa clic su **Disattiva messaggi**, viene aggiunto un attributo **SuppressMessage** nel codice o nel file di eliminazione globale del progetto.

 Il formato dell'attributo **SuppressMessage** è il seguente:

```vb
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>
```

```csharp
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]

```

 [C++]

```
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")

```

 Dove:

- **Categoria regola** : la categoria in cui è definita la regola. Per altre informazioni sulle categorie di regole di analisi del codice, vedere [analisi del codice per gli avvisi del codice gestito](../code-quality/code-analysis-for-managed-code-warnings.md).

- **ID regola** : identificatore della regola. Il supporto include un nome breve e lungo per l'identificatore della regola. Il nome breve è CAXXXX; il nome lungo è CAXXXX: FriendlyTypeName.

- **Giustificazione** : testo utilizzato per documentare il motivo dell'eliminazione del messaggio.

- **ID messaggio** : identificatore univoco di un problema per ogni messaggio.

- **Ambito** : destinazione in cui viene eliminato l'avviso. Se la destinazione non è specificata, viene impostata sulla destinazione dell'attributo. Gli ambiti supportati sono i seguenti:

  - Modulo

  - Spazio dei nomi

  - Risorsa

  - Digitare

  - Member

- **Target** : identificatore utilizzato per specificare la destinazione in cui l'avviso viene eliminato. Deve contenere un nome di elemento completo.

## <a name="suppressmessage-usage"></a>Utilizzo di SuppressMessage
 Gli avvisi di analisi del codice vengono eliminati a livello del quale viene applicata un'istanza dell'attributo **SuppressMessage** . Lo scopo è quello di associare strettamente le informazioni di eliminazione al codice in cui si verifica la violazione.

 Il tipo di eliminazione generale include la categoria Rule e un identificatore di regola che contiene una rappresentazione facoltativa leggibile del nome della regola. Di seguito è riportato un esempio:

 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

 Se sono presenti motivi di prestazioni rigorosi per ridurre al minimo i metadati di eliminazione in origine, il nome della regola può essere escluso. La categoria Rule e l'ID della regola costituiscono insieme un identificatore di regola sufficientemente univoco. Di seguito è riportato un esempio:

 `[SuppressMessage("Microsoft.Design", "CA1039")]`

 Questo formato non è consigliato a causa di problemi di gestibilità.

## <a name="suppressing-multiple-violations-within-a-method-body"></a>Eliminazione di più violazioni all'interno del corpo di un metodo
 Gli attributi possono essere applicati solo a un metodo e non possono essere incorporati all'interno del corpo del metodo. Tuttavia, è possibile specificare l'identificatore come ID del messaggio per distinguere più occorrenze di una violazione all'interno di un metodo.

 [!code-cpp[InSourceSuppression#1](../snippets/cpp/VS_Snippets_CodeAnalysis/InSourceSuppression/cpp/insourcesuppression.cpp#1)]
 [!code-csharp[InSourceSuppression#1](../snippets/csharp/VS_Snippets_CodeAnalysis/InSourceSuppression/cs/InSourceSuppression.cs#1)]
 [!code-vb[InSourceSuppression#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/InSourceSuppression/vb/InSourceSuppression.vb#1)]

## <a name="generated-code"></a>Codice generato
 I compilatori di codice gestito e alcuni strumenti di terze parti generano codice per facilitare lo sviluppo rapido di codice. Il codice generato dal compilatore che viene visualizzato nei file di origine è in genere contrassegnato con l'attributo **GeneratedCodeAttribute** .

 È possibile scegliere se escludere gli avvisi e gli errori di analisi codice per il codice generato. Per informazioni sull'eliminazione di tali avvisi ed errori, vedere [procedura: non visualizzare avvisi per il codice generato](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

 Si noti che l'analisi del codice ignora **GeneratedCodeAttribute** quando viene applicato a un intero assembly o a un singolo parametro. Queste situazioni si verificano raramente.

## <a name="global-level-suppressions"></a>Eliminazione a livello globale
 Lo strumento di analisi del codice gestito esamina gli attributi **SuppressMessage** applicati a livello di assembly, modulo, tipo, membro o parametro. Genera inoltre le violazioni rispetto a risorse e spazi dei nomi. Queste violazioni devono essere applicate a livello globale e sono definite a livello di ambito e di destinazione. Il messaggio seguente, ad esempio, disattiva una violazione dello spazio dei nomi:

 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Quando si elimina un avviso con ambito dello spazio dei nomi, l'avviso viene eliminato rispetto allo spazio dei nomi stesso. Non elimina l'avviso rispetto ai tipi all'interno dello spazio dei nomi.

 Qualsiasi eliminazione può essere espressa specificando un ambito esplicito. Queste evitazioni devono risiedere a livello globale. Non è possibile specificare l'eliminazione a livello di membro decorando un tipo.

 Le evitazioni a livello globale sono l'unico modo per non visualizzare i messaggi che fanno riferimento a codice generato dal compilatore che non esegue il mapping a un'origine utente fornita in modo esplicito. Il codice seguente, ad esempio, evita la violazione di un costruttore emesso dal compilatore:

 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> La destinazione contiene sempre il nome completo dell'elemento.

## <a name="global-suppression-file"></a>File di eliminazione globale
 Il file di eliminazione globale mantiene le eliminazioni che sono eliminazioni a livello globale o eliminazioni che non specificano alcuna destinazione. Ad esempio, le evitazioni per le violazioni a livello di assembly vengono archiviate in questo file. Inoltre, alcune ASP.NET vengono archiviate in questo file perché le impostazioni a livello di progetto non sono disponibili per il code-behind di un form. Viene creata e aggiunta al progetto un'eliminazione globale la prima volta che si seleziona l'opzione **nel file di eliminazione del progetto** del comando non **visualizzare messaggi** nella finestra di elenco errori. Per altre informazioni, vedere [procedura: non visualizzare avvisi tramite la voce di menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md).

## <a name="see-also"></a>Vedere anche
 <xref:System.Diagnostics.CodeAnalysis>
