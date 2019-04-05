---
title: Nella panoramica dell'eliminazione origine | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: 42
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b7f0b3ef2b680dbe4675ef6e8875ef30a1f210bc
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968942"
---
# <a name="in-source-suppression-overview"></a>Panoramica dell'eliminazione nell'origine
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'eliminazione nell'origine è la possibilità di eliminare o Ignora le violazioni di analisi del codice nel codice gestito aggiungendo la **SuppressMessage** i segmenti di codice che provocano le violazioni dell'attributo. Il **SuppressMessage** è un attributo di tipo condizionale che è incluso nei metadati dell'assembly del codice gestito solo se il simbolo di compilazione CODE_ANALYSIS è definito in fase di compilazione.  
  
 In C++/CLI, utilizzare le macro CA_SUPPRESS_MESSAGE o CA_GLOBAL_SUPPRESS_MESSAGE nel file di intestazione per aggiungere l'attributo.  
  
 Non utilizzare le eliminazioni nell'origine nelle build di rilascio per evitare che i metadati di eliminazione nell'origine di spedizione accidentalmente. A causa del costo di elaborazione di eliminazione nell'origine, le prestazioni dell'applicazione possono essere ridotte, includendo i metadati di eliminazione nell'origine.  
  
> [!NOTE]
>  Non è per presentare codice questi attributi se stessi. Per altre informazioni, vedere [Procedura: Eliminare gli avvisi tramite la voce di Menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md). La voce di menu non è disponibile per il codice C++.  
  
## <a name="suppressmessage-attribute"></a>Attributo SuppressMessage  
 Quando si fare doppio clic su un avviso di analisi del codice nel **elenco errori** e quindi fare clic su **Elimina messaggi**, una **SuppressMessage** attributo viene aggiunto a o nel codice il file delle eliminazioni globali del progetto.  
  
 Il **SuppressMessage** attributo presenta il formato seguente:  
  
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
  
-   **Categoria della regola** -la categoria in cui è definita la regola. Per altre informazioni sulle categorie di regole di analisi del codice, vedere [analisi del codice per gli avvisi del codice gestito](../code-quality/code-analysis-for-managed-code-warnings.md).  
  
-   **Id regola** -l'identificatore della regola. Il supporto include sia un nome breve e a lungo per l'identificatore della regola. Il nome breve è CAXXXX; il nome lungo è CAXXXX:FriendlyTypeName.  
  
-   **Giustificazione** -il testo che consente di documentare il motivo dell'eliminazione del messaggio.  
  
-   **Id messaggio** -identificatore univoco di un problema per ogni messaggio.  
  
-   **Ambito** -la destinazione in cui è stato eliminato l'avviso. Se la destinazione non è specificato, cui è impostata la destinazione dell'attributo. Gli ambiti supportati includono quanto segue:  
  
    -   Modulo  
  
    -   Spazio dei nomi  
  
    -   Risorsa  
  
    -   Tipo  
  
    -   Member  
  
-   **Destinazione** : un identificatore che consente di specificare la destinazione in cui è stato eliminato l'avviso. Deve contenere un nome di elemento completo.  
  
## <a name="suppressmessage-usage"></a>Utilizzo SuppressMessage  
 Avvisi dell'analisi codice vengono soppressi a livello di a cui un'istanza di **SuppressMessage** viene applicato l'attributo. Lo scopo di questo è uno stretto accoppiamento le informazioni di eliminazione per il codice in cui si verifica la violazione.  
  
 Il formato generale dell'eliminazione include la categoria della regola e un identificatore di regola che contiene una rappresentazione leggibile facoltativa del nome della regola. Ad esempio,  
  
 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 Se esistono motivi di prestazioni strict per ridurre al minimo i metadati di eliminazione nell'origine, il nome della regola stessa può essere omesso. La categoria della regola e il relativo ID regola insieme costituiscono un identificatore di regola sufficientemente univoco. Ad esempio,  
  
 `[SuppressMessage("Microsoft.Design", "CA1039")]`  
  
 Questo formato non è consigliato a causa di problemi di gestibilità.  
  
## <a name="suppressing-multiple-violations-within-a-method-body"></a>Eliminazione di più violazioni all'interno di un corpo del metodo  
 Gli attributi possono essere applicati solo a un metodo e non possono essere incorporati all'interno del corpo del metodo. Tuttavia, è possibile specificare l'identificatore come ID di messaggio per distinguere più occorrenze di una violazione all'interno di un metodo.  
  
 [!code-cpp[InSourceSuppression#1](../snippets/cpp/VS_Snippets_CodeAnalysis/InSourceSuppression/cpp/insourcesuppression.cpp#1)]
 [!code-csharp[InSourceSuppression#1](../snippets/csharp/VS_Snippets_CodeAnalysis/InSourceSuppression/cs/InSourceSuppression.cs#1)]
 [!code-vb[InSourceSuppression#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/InSourceSuppression/vb/InSourceSuppression.vb#1)]  
  
## <a name="generated-code"></a>Codice generato  
 I compilatori di codice gestito e alcuni strumenti di terze parti generano codice per facilitare lo sviluppo rapido di codice. Il codice generato dal compilatore che viene visualizzato nel file di origine in genere è contrassegnato con il **GeneratedCodeAttribute** attributo.  
  
 È possibile scegliere se eliminare gli avvisi dell'analisi codice e gli errori per il codice generato. Per informazioni su come eliminare questi avvisi ed errori, vedere [come: Non visualizzare avvisi per il codice generato](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).  
  
 Si noti che l'analisi del codice ignora **GeneratedCodeAttribute** quando viene applicata a un intero assembly o un singolo parametro. Queste situazioni si verificano raramente.  
  
## <a name="global-level-suppressions"></a>Eliminazioni a livello globale  
 Lo strumento di analisi codice gestito viene esaminato **SuppressMessage** gli attributi applicati a livello di assembly, modulo, tipo, membro o parametro. Viene inoltre generato violazioni contro le risorse e gli spazi dei nomi. Tali violazioni deve essere applicati a livello globale e sono con ambiti e di destinazione. Ad esempio, il messaggio seguente elimina una violazione dello spazio dei nomi:  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`  
  
> [!NOTE]
>  Quando si elimina un avviso con ambito spazio dei nomi, viene eliminato l'avviso per lo spazio dei nomi stesso. Non elimina l'avviso in base a tipi nello spazio dei nomi.  
  
 Qualsiasi eliminazione può essere espresse specificando un ambito esplicito. È necessario in tempo reale di queste eliminazioni a livello globale. È possibile specificare l'eliminazione a livello di membro tramite la decorazione di un tipo.  
  
 Eliminazioni a livello globale sono l'unico modo per eliminare i messaggi che fanno riferimento al codice generato dal compilatore che non esegue il mapping a un'origine utente specificato in modo esplicito. Ad esempio, il codice seguente elimina una violazione in base a un costruttore emesso dal compilatore:  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`  
  
> [!NOTE]
>  La destinazione contiene sempre il nome dell'elemento completo.  
  
## <a name="global-suppression-file"></a>File eliminazione globale  
 Il file di eliminazione globale conserva le eliminazioni a livello globale o le eliminazioni che non si specificano una destinazione. Ad esempio, in questo file vengono archiviate le eliminazioni per le violazioni del livello assembly. Inoltre, alcune eliminazioni ASP.NET vengono archiviate in questo file perché le impostazioni a livello di progetto non sono disponibili per un modello code-behind. Eliminazione globale viene creata e aggiunto al progetto la prima volta che si seleziona il **File di progetto eliminazione** opzione del **Elimina messaggi** comando nella finestra Elenco errori. Per altre informazioni, vedere [Procedura: Eliminare gli avvisi tramite la voce di Menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Diagnostics.CodeAnalysis>
