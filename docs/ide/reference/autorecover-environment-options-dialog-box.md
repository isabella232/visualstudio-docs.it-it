---
title: Salvataggio automatico, Ambiente, finestra di dialogo Opzioni
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.DialogAutoRestore
- VS.ToolsOptionsPages.Environment.AutoRecover
- VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore
helpviewer_keywords:
- files, recovering
- AutoRecover page
- saving files, automatically
- files, saving automatically
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c6b65da35a180e507af8175d7e1c8e209e84ba8d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54993988"
---
# <a name="autorecover-environment-options-dialog-box"></a>Salvataggio automatico, Ambiente, finestra di dialogo Opzioni

Usare questa pagina nella finestra di dialogo **Opzioni** per specificare se eseguire o meno il backup automatico dei file. È anche possibile specificare se i file modificati devono essere ripristinati nel caso in cui Visual Studio si arresti in modo imprevisto.

Per accedere a questa finestra di dialogo, selezionare il menu **Strumenti**, **Opzioni** e quindi **Ambiente** > **Salvataggio automatico**. Se questa pagina non appare nell'elenco, selezionare **Mostra tutte le impostazioni** nella finestra di dialogo **Opzioni**.

**Salva automaticamente le informazioni ogni [n] minuti**

Usare questa opzione per personalizzare la frequenza con cui un file viene salvato automaticamente nell'editor. Per i file salvati in precedenza, una copia del file viene salvata in *%USERPROFILE%\Documenti\Visual Studio \\[versione]\File di backup\\*[nomeprogetto]. Se si tratta di un nuovo file che non è ancora stato salvato, il file viene salvato automaticamente assegnando un nome file generato in modo casuale.

**Mantieni informazioni di salvataggio automatico per [n] giorni**

Usare questa opzione per specificare per quanto tempo i file creati per il salvataggio automatico devono restare memorizzati in Visual Studio.

### <a name="see-also"></a>Vedere anche

- [Finestra di dialogo Opzioni](../../ide/reference/options-dialog-box-visual-studio.md)