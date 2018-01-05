---
title: In panoramica di eliminazione origine | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 92babbf3c7a5863d178463b69525bdb722bf28ad
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="in-source-suppression-overview"></a>Panoramica dell'eliminazione nell'origine
Eliminazione in origine è la possibilità di eliminare o ignorare le violazioni di analisi del codice nel codice gestito mediante l'aggiunta di **SuppressMessage** attributo per i segmenti di codice che provocano le violazioni. Il **SuppressMessage** è un attributo condizionale incluso nei metadati dell'assembly del codice gestito solo se il simbolo di compilazione CODE_ANALYSIS è definito in fase di compilazione.  
  
 In C++/CLI, utilizzare le macro CA_SUPPRESS_MESSAGE o CA_GLOBAL_SUPPRESS_MESSAGE nel file di intestazione per aggiungere l'attributo.  
  
 Non utilizzare eliminazioni nell'origine nella build di rilascio per evitare che i metadati di eliminazione nell'origine di spedizione accidentalmente. A causa del costo di elaborazione dell'eliminazione nell'origine, le prestazioni dell'applicazione possono essere ridotte includendo i metadati di eliminazione nell'origine.  
  
> [!NOTE]
>  Non è in codice questi attributi manualmente. Per ulteriori informazioni, vedere [procedura: esclusione di avvisi tramite la voce di Menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md). La voce di menu non è disponibile per il codice C++.  
  
## <a name="suppressmessage-attribute"></a>SuppressMessage (attributo)  
 Quando si fa clic su un avviso di analisi del codice nel **elenco errori** e quindi fare clic su **Elimina messaggi**, **SuppressMessage** attributo viene aggiunto nel codice o per il file delle eliminazioni globali del progetto.  
  
 Il **SuppressMessage** presenta il formato seguente:  
  
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
  
-   **Categoria della regola** -la categoria in cui la regola è definita. Per ulteriori informazioni sulle categorie di regole di analisi codice, vedere [Code Analysis for Managed Code Warnings](../code-quality/code-analysis-for-managed-code-warnings.md).  
  
-   **Id regola** -l'identificatore della regola. Il supporto include sia un nome breve e a lungo per l'identificatore della regola. Il nome breve è CAXXXX: NOMETIPODESCRITTIVO; il nome lungo è CAXXXX:FriendlyTypeName.  
  
-   **Giustificazione** -il testo che viene utilizzato per documentare il motivo dell'eliminazione del messaggio.  
  
-   **Id messaggio** -identificatore univoco di un problema per ogni messaggio.  
  
-   **Ambito** -la destinazione in cui è stato eliminato l'avviso. Se la destinazione non è specificata, cui è impostata la destinazione dell'attributo. Gli ambiti supportati includono:  
  
    -   Modulo  
  
    -   Spazio dei nomi  
  
    -   Risorsa  
  
    -   Tipo  
  
    -   Member  
  
-   **Destinazione** : identificatore utilizzato per specificare la destinazione in cui è stato eliminato l'avviso. Deve contenere un nome completo di elementi.  
  
## <a name="suppressmessage-usage"></a>Utilizzo di SuppressMessage  
 Avvisi dell'analisi del codice vengono eliminati al livello a cui un'istanza di **SuppressMessage** attributo viene applicato. Lo scopo di questo è strettamente accoppiato le informazioni di eliminazione per il codice in cui si verifica la violazione.  
  
 Il formato generale dell'eliminazione include la categoria della regola e un identificatore di regola che contiene una rappresentazione leggibile facoltativa del nome della regola. Ad esempio,  
  
 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 Se non esistono motivi di prestazioni strict per ridurre al minimo i metadati di eliminazione nell'origine, il nome della regola può essere omesso. La categoria della regola e il relativo ID regola insieme costituiscono un sufficientemente identificatore univoco della regola. Ad esempio,  
  
 `[SuppressMessage("Microsoft.Design", "CA1039")]`  
  
 Questo formato non è consigliato a causa di problemi di gestibilità.  
  
## <a name="suppressing-multiple-violations-within-a-method-body"></a>Eliminazione di più violazioni all'interno di un corpo del metodo  
 Gli attributi possono essere applicati solo a un metodo e non possono essere incorporati all'interno del corpo del metodo. Tuttavia, è possibile specificare l'identificatore come ID di messaggio per distinguere più occorrenze di una violazione in un metodo.  
  
 [!code-cpp[InSourceSuppression#1](../code-quality/codesnippet/CPP/in-source-suppression-overview_1.cpp)]
 [!code-vb[InSourceSuppression#1](../code-quality/codesnippet/VisualBasic/in-source-suppression-overview_1.vb)]
 [!code-csharp[InSourceSuppression#1](../code-quality/codesnippet/CSharp/in-source-suppression-overview_1.cs)]  
  
## <a name="generated-code"></a>Codice generato  
 I compilatori di codice gestito e alcuni strumenti di terze parti generano codice per facilitare lo sviluppo rapido del codice. Codice generato dal compilatore che viene visualizzato nel file di origine in genere è contrassegnato con il **GeneratedCodeAttribute** attributo.  
  
 È possibile scegliere se eliminare gli avvisi di analisi del codice e gli errori per il codice generato. Per informazioni sull'eliminazione di tali avvisi ed errori, vedere [procedura: esclusione di avvisi per il codice generato](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).  
  
 Si noti che l'analisi del codice ignora **GeneratedCodeAttribute** quando applicato a un intero assembly o un singolo parametro. Questi casi si verificano raramente.  
  
## <a name="global-level-suppressions"></a>Eliminazioni a livello globale  
 Lo strumento di analisi codice gestito viene esaminato **SuppressMessage** gli attributi applicati a livello di assembly, modulo, tipo, membro o parametro. Viene inoltre generato violazioni risorse e gli spazi dei nomi. Tali violazioni devono essere applicate a livello globale e hanno come ambite e di destinazione. Ad esempio, il messaggio seguente elimina una violazione dello spazio dei nomi:  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`  
  
> [!NOTE]
>  Quando si elimina un avviso con ambito spazio dei nomi, viene eliminato l'avviso sullo spazio dei nomi stesso. Non elimina l'avviso con i tipi nello spazio dei nomi.  
  
 Qualsiasi eliminazione può essere espresso specificando un ambito esplicito. Queste eliminazioni devono avvenire a livello globale. È possibile specificare a livello di membro eliminazione tramite la decorazione di un tipo.  
  
 Eliminazioni a livello globale sono l'unico modo per eliminare i messaggi che fanno riferimento al codice generato dal compilatore che non eseguono il mapping a un'origine utente specificato in modo esplicito. Ad esempio, il codice seguente elimina una violazione in un costruttore emesso dal compilatore:  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`  
  
> [!NOTE]
>  La destinazione contiene sempre il nome completo dell'elemento.  
  
## <a name="global-suppression-file"></a>File eliminazione globale  
 Il file eliminazione globale gestisce le eliminazioni a livello globale o le eliminazioni che non si specificano una destinazione. Ad esempio, in questo file vengono archiviate le eliminazioni per le violazioni a livello di assembly. Inoltre, alcune eliminazioni ASP.NET vengono memorizzate in questo file perché le impostazioni a livello di progetto non sono disponibili per un modello code-behind. Un'eliminazione globale viene creata e aggiunto al progetto la prima volta che si seleziona il **File di eliminazione In progetto** opzione del **Elimina messaggi** comando nella finestra Elenco errori. Per ulteriori informazioni, vedere [procedura: esclusione di avvisi tramite la voce di Menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Diagnostics.CodeAnalysis>