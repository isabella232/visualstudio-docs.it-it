---
title: Salvataggio automatico, Ambiente, finestra di dialogo Opzioni
description: Informazioni sulla finestra di dialogo Ripristino automatico, Ambiente, Opzioni e su come viene usata per specificare se eseguire automaticamente il backup dei file.
ms.custom: SEO-VS-2020
ms.date: 08/14/2020
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
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: af89cfb0e47655e5deac867e5eeec1da255408c27d6037468ad8e42f8fe31c8a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121400251"
---
# <a name="autorecover-environment-options-dialog-box"></a>Salvataggio automatico, Ambiente, finestra di dialogo Opzioni

Usare questa pagina nella finestra di dialogo **Opzioni** per specificare se eseguire o meno il backup automatico dei file. È anche possibile specificare se i file modificati devono essere ripristinati nel caso in cui Visual Studio si arresti in modo imprevisto.

Per accedere a questa finestra di dialogo, passare a **Strumenti**  >  **Opzioni**  >  **Ambiente** Salvataggio  >  **automatico.**

:::image type="content" source="media/autorecover-options.png" alt-text="Screenshot della sezione Salvataggio automatico nella finestra di dialogo Opzioni":::

**Salva automaticamente le informazioni ogni [n] minuti**

::: moniker range=">=vs-2022"

Usare questa opzione per personalizzare la frequenza con cui un file viene salvato automaticamente nell'editor. Per i file salvati Visual Studio salva una copia del file in ***%LocalAppData%\Microsoft\VisualStudio\BackupFiles \\ [nomeprogetto]***. Se il file è nuovo e non è ancora stato salvato, Visual Studio lo salva automaticamente usando un nome file generato in modo casuale.

::: moniker-end

::: moniker range="vs-2019"

Usare questa opzione per personalizzare la frequenza con cui un file viene salvato automaticamente nell'editor. Per i file salvati in precedenza, Visual Studio 2019 versione 16.2 e successive salva una copia del file in ***%LocalAppData%\Microsoft\VisualStudio\BackupFiles \\ [nomeprogetto]***. Se il file è nuovo e non è ancora stato salvato, Visual Studio lo salva automaticamente usando un nome file generato in modo casuale.

> [!NOTE]
> Se si usa Visual Studio 2019 versione 16.1 o precedente, il percorso del file è *%USERPROFILE%\Documents\Visual Studio [versione]\File di backup \\ [nomeprogetto]*. Per altre informazioni, vedere la pagina Visual Studio cronologia delle note sulla versione [2019.](/visualstudio/releases/2019/release-notes-history/)

::: moniker-end

::: moniker range="vs-2017"

Usare questa opzione per personalizzare la frequenza con cui un file viene salvato automaticamente nell'editor. Per i file salvati in precedenza, Visual Studio 2017 salva una copia del file in *%USERPROFILE%\Documents\Visual Studio [versione]\File di backup \\ [nomeprogetto]*. Se il file è nuovo e non è ancora stato salvato, Visual Studio lo salva automaticamente usando un nome file generato in modo casuale.

::: moniker-end

**Mantieni le informazioni di salvataggio automatico per [n] giorni**

Usare questa opzione per specificare per quanto tempo i file creati per il salvataggio automatico devono restare memorizzati in Visual Studio.

### <a name="see-also"></a>Vedi anche

- [Opzioni (finestra di dialogo)](../../ide/reference/options-dialog-box-visual-studio.md)
