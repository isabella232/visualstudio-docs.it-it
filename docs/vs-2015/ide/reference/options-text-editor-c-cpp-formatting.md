---
title: Opzioni, Editor di testo, C/C++, Formattazione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- C++
helpviewer_keywords:
- Text Editor Options dialog box, formatting
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5ad06dfb32c301985eb4976f6c89c7be1e0e68da
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662337"
---
# <a name="options-text-editor-cc-formatting"></a>Opzioni, Editor di testo, C/C++, Formattazione
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Consente di modificare il comportamento predefinito dell'editor di codice in fase di programmazione in C o C++.

 Per accedere a questa pagina, nel riquadro sinistro della finestra di dialogo **Opzioni** espandere **Editor di testo** e **C/C++**, quindi fare clic su **Formattazione**.

> [!NOTE]
> Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [personalizzazione delle impostazioni di sviluppo in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="cc-options"></a>Opzioni C/C++
 **Abilitare le descrizioni comandi delle informazioni rapide automatiche** Abilita o Disabilita la funzionalità di IntelliSense per informazioni rapide.

## <a name="inactive-code"></a>Codice inattivo
 **Mostra blocchi di codice inattivi** Il codice inattivo a causa di `#ifdef` dichiarazioni è colorato in modo diverso per facilitarne l'identificazione.

 **Disabilitare l'opacità del codice inattivo** Il codice inattivo può essere identificato usando il colore anziché la trasparenza.

 **Percentuale di opacità del codice inattivo** È possibile personalizzare il grado di opacità per i blocchi di codice inattivi.

## <a name="indentation"></a>Rientro
 **Rientro parentesi graffe** È possibile configurare la modalità di allineamento delle parentesi graffe quando si preme INVIO dopo aver avviato un blocco di codice, ad esempio una funzione o un `for` ciclo. Le parentesi graffe possono essere allineate al primo carattere del blocco di codice oppure rientrate.

 **Rientro automatico nella scheda** È possibile configurare cosa accade nella riga di codice corrente quando si preme TAB. La riga viene rientrata oppure viene inserito un carattere di tabulazione.

## <a name="miscellaneous"></a>Varie
 **Enumerare i commenti nella finestra elenco attività** L'editor può analizzare i file Open Source per le parole preimpostate nei commenti. Crea una voce nella finestra **Elenco attività** per qualsiasi parola chiave trovata.

 **Evidenziare i token corrispondenti** Quando il cursore è accanto a una parentesi graffa, l'editor può evidenziare la parentesi graffa corrispondente in modo che sia possibile visualizzare più facilmente il codice contenuto.

## <a name="outlining"></a>struttura
 Attiva **modalità struttura all'apertura dei file** Quando si porta un file nell'editor di testo, è possibile abilitare la funzionalità di struttura. Per altre informazioni, vedere [Struttura](../../ide/outlining.md). Se questa opzione è selezionata, la funzionalità di struttura verrà abilitata all'apertura di un file.

 **Struttura automatica dei blocchi di area #pragma** Quando questa opzione è selezionata, la struttura automatica per le [direttive pragma](https://msdn.microsoft.com/library/9867b438-ac64-4e10-973f-c3955209873f) è abilitata. In questo modo è possibile espandere o comprimere blocchi pragma region in modalità struttura.

 **Struttura automatica dei blocchi di istruzioni** Quando questa opzione è selezionata, la struttura automatica è abilitata per i costrutti di istruzione seguenti:

- [if-else](https://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2)

- [Istruzione switch (C++)](https://msdn.microsoft.com/library/6c3f3ed3-5593-463c-8f4b-b33742b455c6)

- [Istruzione while (C++)](https://msdn.microsoft.com/library/358dbe76-5e5e-4af5-b575-c2293c636899)

## <a name="see-also"></a>Vedere anche
 [Generale, ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md) [con IntelliSense](../../ide/using-intellisense.md)
