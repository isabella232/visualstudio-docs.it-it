---
title: Frammenti di codice Visual C# | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snippets [C#], default snippets
- snippets [C#], Code Snippet Inserter
- Code Snippet Inserter [J#]
- Code Snippet Inserter [C#]
- Visual C#, default snippets
ms.assetid: dbea3dd6-e650-4190-b874-c9f097d7de6e
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2afbadccfc894dd5ba5baba9c58ab43417f44ed5
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/05/2018
ms.locfileid: "47590727"
---
# <a name="visual-c-code-snippets"></a>Frammenti di codice Visual C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [frammenti di codice Visual c#](https://docs.microsoft.com/visualstudio/ide/visual-csharp-code-snippets).  
  
I frammenti di codice sono piccole porzioni di codice pronte all'uso che si possono inserire rapidamente nel codice. Ad esempio, il frammento di codice `for` crea un ciclo `for` vuoto. Alcuni frammenti di codice sono frammenti racchiusi, che consentono di selezionare righe di codice e quindi scegliere un frammento di codice che incorpora le righe di codice selezionate. Ad esempio, quando si selezionano righe di codice e si attiva il frammento di codice `for`, viene creato un ciclo `for` con le righe di codice all'interno del blocco del ciclo. I frammenti di codice possono rendere la scrittura del codice dei programmi più veloce, più semplice e più affidabile.  
  
 È possibile inserire un frammento di codice nella posizione del cursore o un frammento di codice racchiuso intorno al codice attualmente selezionato. Lo strumento per l'inserimento dei frammenti di codice viene richiamato usando i comandi **Inserisci frammento di codice** o **Racchiudi tra** del menu **IntelliSense** o usando i tasti di scelta rapida CTRL+K e quindi X o CTRL+K e quindi S rispettivamente.  
  
 Lo strumento per l'inserimento dei frammenti di codice visualizza il nome del frammento di codice per tutti i frammenti di codice disponibili. Lo strumento include anche una finestra di dialogo di input in cui è possibile digitare il nome del frammento di codice o parte del nome del frammento di codice. Lo strumento per l'inserimento dei frammenti di codice evidenzia la corrispondenza più prossima al nome di un frammento di codice. Quando si preme TAB in qualsiasi momento lo strumento per l'inserimento dei frammenti di codice viene chiuso e viene inserito il frammento di codice attualmente selezionato. Se si preme ESC o si fa clic con il mouse nell'Editor di codice, lo strumento per l'inserimento dei frammenti di codice viene chiuso senza inserire un frammento di codice.  
  
## <a name="default-code-snippets"></a>Frammenti di codice predefiniti  
 Per impostazione predefinita in Visual Studio sono inclusi i frammenti di codice riportati di seguito.  
  
|Nome (o collegamento)|Descrizione|Percorsi validi per l'inserimento del frammento di codice|  
|--------------------------|-----------------|---------------------------------------|  
|#if|Crea una direttiva [#if](http://msdn.microsoft.com/library/48cabbff-ca82-491f-a56a-eeccd528c7c2) e una direttiva [#endif](http://msdn.microsoft.com/library/6a5fca55-5aee-441f-86f6-1c99fbe9ec05).|Ovunque.|  
|#region|Crea una direttiva [#region](http://msdn.microsoft.com/library/672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4) e una direttiva [#endregion](http://msdn.microsoft.com/library/16099660-91b2-49e5-9646-77f9ef069526).|Ovunque.|  
|~|Crea un distruttore per la classe contenitore.|All'interno di una classe.|  
|Attributo|Crea una dichiarazione per una classe che deriva da <xref:System.Attribute>.|All'interno di uno spazio dei nomi (incluso lo spazio dei nomi globale), una classe o uno struct.|  
|checked|Crea un blocco [checked](http://msdn.microsoft.com/library/718a1194-988d-48a3-b089-d6ee8bd1608d).|All'interno di un metodo, un indicizzatore, una funzione di accesso proprietà o una funzione di accesso eventi.|  
|classe|Crea una dichiarazione di classe.|All'interno di uno spazio dei nomi (incluso lo spazio dei nomi globale), una classe o uno struct.|  
|ctor|Crea un costruttore per la classe contenitore.|All'interno di una classe.|  
|cw|Crea una chiamata a <xref:System.Console.WriteLine%2A>.|All'interno di un metodo, un indicizzatore, una funzione di accesso proprietà o una funzione di accesso eventi.|  
|do|Crea una [scopo](http://msdn.microsoft.com/library/50725f79-9ba6-4898-aa78-6e331568a1bb) `while` ciclo.|All'interno di un metodo, un indicizzatore, una funzione di accesso proprietà o una funzione di accesso eventi.|  
|else|Crea un blocco [else](http://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2).|All'interno di un metodo, un indicizzatore, una funzione di accesso proprietà o una funzione di accesso eventi.|  
|enum|Crea una dichiarazione [enum](http://msdn.microsoft.com/library/bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c).|All'interno di uno spazio dei nomi (incluso lo spazio dei nomi globale), una classe o uno struct.|  
|equals|Crea una dichiarazione di metodo che esegue l'override del metodo <xref:System.Object.Equals%2A> definito nella classe <xref:System.Object>.|All'interno di una classe o uno struct.|  
|exception|Crea una dichiarazione per una classe che deriva da un'eccezione (<xref:System.Exception> per impostazione predefinita).|All'interno di uno spazio dei nomi (incluso lo spazio dei nomi globale), una classe o uno struct.|  
|for|Crea un ciclo [for](http://msdn.microsoft.com/library/34041a40-2c87-467a-9ffb-a0417d8f67a8).|All'interno di un metodo, un indicizzatore, una funzione di accesso proprietà o una funzione di accesso eventi.|  
|foreach|Crea un ciclo [foreach](http://msdn.microsoft.com/library/5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec).|All'interno di un metodo, un indicizzatore, una funzione di accesso proprietà o una funzione di accesso eventi.|  
|forr|Crea un ciclo [for](http://msdn.microsoft.com/library/34041a40-2c87-467a-9ffb-a0417d8f67a8) che decrementa la variabile di ciclo dopo ogni iterazione.|All'interno di un metodo, un indicizzatore, una funzione di accesso proprietà o una funzione di accesso eventi.|  
|if|Crea un blocco [if](http://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2).|All'interno di un metodo, un indicizzatore, una funzione di accesso proprietà o una funzione di accesso eventi.|  
|indicizzatore|Crea una dichiarazione di indicizzatore.|All'interno di una classe o uno struct.|  
|interfaccia|Crea una dichiarazione [interface](http://msdn.microsoft.com/library/7da38e81-4f99-4bc5-b07d-c986b687eeba).|All'interno di uno spazio dei nomi (incluso lo spazio dei nomi globale), una classe o uno struct.|  
|invoke|Crea un blocco che richiama in modo sicuro un evento.|All'interno di un metodo, un indicizzatore, una funzione di accesso proprietà o una funzione di accesso eventi.|  
|iteratore|Crea un iteratore.|All'interno di una classe o uno struct.|  
|iterindex|Crea una coppia iteratore/indicizzatore "denominata" usando una classe annidata.|All'interno di una classe o uno struct.|  
|blocco|Crea un blocco [lock](http://msdn.microsoft.com/library/656da1a4-707e-4ef6-9c6e-6d13b646af42).|All'interno di un metodo, un indicizzatore, una funzione di accesso proprietà o una funzione di accesso eventi.|  
|mbox|Crea una chiamata a <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName>. Può essere necessario aggiungere un riferimento a System.Windows.Forms.dll.|All'interno di un metodo, un indicizzatore, una funzione di accesso proprietà o una funzione di accesso eventi.|  
|namespace|Crea una dichiarazione [namespace](http://msdn.microsoft.com/library/0a788423-9110-42e0-97d9-bda41ca4870f).|All'interno di uno spazio dei nomi (incluso lo spazio dei nomi globale).|  
|prop|Crea una dichiarazione di [proprietà implementata automaticamente](http://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7).|All'interno di una classe o uno struct.|  
|propfull|Crea una dichiarazione di proprietà con le funzioni di accesso get e set.|All'interno di una classe o uno struct.|  
|propg|Crea una [proprietà implementata automaticamente](http://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7) di sola lettura con una funzione di accesso "set" privata.|All'interno di una classe o uno struct.|  
|sim|Crea una dichiarazione [static](http://msdn.microsoft.com/library/5509e215-2183-4da3-bab4-6b7e607a4fdf)[int](http://msdn.microsoft.com/library/212447b4-5d2a-41aa-88ab-84fe710bdb52) del metodo Main.|All'interno di una classe o uno struct.|  
|struct|Crea una dichiarazione [struct](http://msdn.microsoft.com/library/ff3dd9b7-dc93-4720-8855-ef5558f65c7c).|All'interno di uno spazio dei nomi (incluso lo spazio dei nomi globale), una classe o uno struct.|  
|svm|Crea una dichiarazione [static](http://msdn.microsoft.com/library/5509e215-2183-4da3-bab4-6b7e607a4fdf)[void](http://msdn.microsoft.com/library/0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4) del metodo Main.|All'interno di una classe o uno struct.|  
|switch|Crea un blocco [switch](http://msdn.microsoft.com/library/44bae8b8-8841-4d85-826b-8a94277daecb).|All'interno di un metodo, un indicizzatore, una funzione di accesso proprietà o una funzione di accesso eventi.|  
|try|Crea un blocco [try-catch](http://msdn.microsoft.com/library/cb5503c7-bfa1-4610-8fc2-ddcd2e84c438).|All'interno di un metodo, un indicizzatore, una funzione di accesso proprietà o una funzione di accesso eventi.|  
|tryf|Crea un blocco [try-finally](http://msdn.microsoft.com/library/c27623fb-7261-4464-862c-7a369d3c8f0a).|All'interno di un metodo, un indicizzatore, una funzione di accesso proprietà o una funzione di accesso eventi.|  
|unchecked|Crea un blocco [unchecked](http://msdn.microsoft.com/library/0c021f7c-923f-4b3d-a58f-55336f5ac27e).|All'interno di un metodo, un indicizzatore, una funzione di accesso proprietà o una funzione di accesso eventi.|  
|unsafe|Crea un blocco [unsafe](http://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0).|All'interno di un metodo, un indicizzatore, una funzione di accesso proprietà o una funzione di accesso eventi.|  
|utilizzo|Crea una direttiva [using](http://msdn.microsoft.com/library/b42b8e61-5e7e-439c-bb71-370094b44ae8).|All'interno di uno spazio dei nomi (incluso lo spazio dei nomi globale).|  
|while|Crea un ciclo [while](http://msdn.microsoft.com/library/72a0765c-6852-4aca-b327-4a11cb7f5c59).|All'interno di un metodo, un indicizzatore, una funzione di accesso proprietà o una funzione di accesso eventi.|  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni dei frammenti di codice](../ide/code-snippet-functions.md)   
 [Frammenti di codice](../ide/code-snippets.md)   
 [Procedura: Creare un nuovo frammento con sostituzioni](http://msdn.microsoft.com/en-us/8d56d43c-097a-475b-aa85-cae1554b6338)   
 [Parametri di modello](../ide/template-parameters.md)   
 [Procedura: usare frammenti di codice racchiusi](../ide/how-to-use-surround-with-code-snippets.md)   
 [Procedura: Ripristinare refactoring di frammenti C#](../ide/how-to-restore-csharp-refactoring-snippets.md)



