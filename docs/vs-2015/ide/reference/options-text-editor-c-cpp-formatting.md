---
title: Opzioni, Editor di testo, C/C++, Formattazione | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- C++
helpviewer_keywords:
- Text Editor Options dialog box, formatting
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 28bbc6d68d55fd76f27957a0a1ab4626dad95b66
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518589"
---
# <a name="options-text-editor-cc-formatting"></a>Opzioni, Editor di testo, C/C++, Formattazione
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [opzioni, Editor di testo, C/C++, formattazione](https://docs.microsoft.com/visualstudio/ide/reference/options-text-editor-c-cpp-formatting).  
  
  
Consente di modificare il comportamento predefinito dell'editor di codice in fase di programmazione in C o C++.  
  
 Per accedere a questa pagina, nel riquadro sinistro della finestra di dialogo **Opzioni** espandere **Editor di testo** e **C/C++**, quindi fare clic su **Formattazione**.  
  
> [!NOTE]
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="cc-options"></a>Opzioni C/C++  
 **Attiva descrizione comandi per informazioni rapide automatiche**  
 Consente di abilitare o disabilitare la funzionalità Informazioni rapide di IntelliSense.  
  
## <a name="inactive-code"></a>Codice inattivo  
 **Mostra blocchi inattivi**  
 Per il codice reso inattivo da dichiarazioni `#ifdef` viene utilizzato un colore diverso in modo da agevolarne l'identificazione.  
  
 **Disabilita opacità del codice inattivo**  
 Codice inattivo che può essere identificato tramite colore, anziché tramite trasparenza.  
  
 **Percentuale di opacità del codice inattivo**  
 È possibile personalizzare il grado di opacità per blocchi di codice inattivo.  
  
## <a name="indentation"></a>Rientro  
 **Rientra parentesi graffe**  
 È possibile configurare la modalità di allineamento delle parentesi graffe quando si preme INVIO dopo aver avviato un blocco di codice, ad esempio una funzione o un ciclo `for`. Le parentesi graffe possono essere allineate al primo carattere del blocco di codice oppure rientrate.  
  
 **Rientra alla pressione del tasto TAB**  
 È possibile configurare le operazioni eseguite nella riga di codice corrente quando si preme TAB. La riga viene rientrata oppure viene inserito un carattere di tabulazione.  
  
## <a name="miscellaneous"></a>Varie  
 **Enumera attività di commento**  
 L'editor può analizzare le parole preimpostate nei commenti all'interno dei file di origine aperti. Crea una voce nella finestra **Elenco attività** per qualsiasi parola chiave trovata.  
  
 **Evidenzia token corrispondenti**  
 Se il cursore si trova accanto a una parentesi graffa, l'editor può evidenziare la parentesi graffa corrispondente in modo che sia possibile visualizzare più agevolmente il codice contenuto.  
  
## <a name="outlining"></a>struttura  
 **Attiva modalità struttura all'apertura del file**  
 Aprendo un file nell'editor di testo, è possibile abilitare la funzionalità di struttura. Per altre informazioni, vedere [Struttura](../../ide/outlining.md). Se questa opzione è selezionata, la funzionalità di struttura verrà abilitata all'apertura di un file.  
  
 **Struttura blocchi pragma region**  
 Se questa opzione è selezionata, la struttura automatica per le [direttive pragma](http://msdn.microsoft.com/library/9867b438-ac64-4e10-973f-c3955209873f) è abilitata. In questo modo è possibile espandere o comprimere blocchi pragma region in modalità struttura.  
  
 **Struttura blocchi di istruzioni**  
 Se questa opzione è selezionata, la struttura automatica è abilitata per i costrutti delle istruzioni seguenti:  
  
-   [if-else](http://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2)  
  
-   [Istruzione switch (C++)](http://msdn.microsoft.com/library/6c3f3ed3-5593-463c-8f4b-b33742b455c6)  
  
-   [Istruzione while (C++)](http://msdn.microsoft.com/library/358dbe76-5e5e-4af5-b575-c2293c636899)  
  
## <a name="see-also"></a>Vedere anche  
 [General, Environment, Options Dialog Box](../../ide/reference/general-environment-options-dialog-box.md)  (Generale, Ambiente, finestra di dialogo Opzioni)  
 [Utilizzo di IntelliSense](../../ide/using-intellisense.md)



