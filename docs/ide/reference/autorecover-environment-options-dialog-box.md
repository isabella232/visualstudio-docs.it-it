---
title: Salvataggio automatico, Ambiente, finestra di dialogo Opzioni
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f35424089b293b858c609d19f59459693373eb4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "88250284"
---
# <a name="autorecover-environment-options-dialog-box"></a>Salvataggio automatico, Ambiente, finestra di dialogo Opzioni

Usare questa pagina nella finestra di dialogo **Opzioni** per specificare se eseguire o meno il backup automatico dei file. È anche possibile specificare se i file modificati devono essere ripristinati nel caso in cui Visual Studio si arresti in modo imprevisto.

Per accedere a questa finestra di dialogo, passare a **strumenti**  >  **Opzioni**  >  **ambiente**  >  **Ripristino automatico**.

:::image type="content" source="media/autorecover-options.png" alt-text="Screenshot della sezione autocover nella finestra di dialogo Opzioni":::

**Salva automaticamente le informazioni ogni [n] minuti**

::: moniker range="vs-2019"

Usare questa opzione per personalizzare la frequenza con cui un file viene salvato automaticamente nell'editor. Per i file salvati in precedenza, Visual Studio 2019 versione 16,2 e successive salva una copia del file in ***%LocalAppData%\Microsoft\VisualStudio\BackupFiles \\ [NomeProgetto]***. Se il file è nuovo e non è ancora stato salvato, Visual Studio lo salva automaticamente usando un nome file generato in modo casuale.

> [!NOTE]
> Se si usa Visual Studio 2019 versione 16,1 o precedente, il percorso del file è *%USERPROFILE%\Documents\Visual Studio [versione] \backup file \\ [NomeProgetto]*. Per ulteriori informazioni, vedere la pagina della [cronologia delle note sulla versione di Visual Studio 2019](/visualstudio/releases/2019/release-notes-history/) .

::: moniker-end

::: moniker range="vs-2017"

Usare questa opzione per personalizzare la frequenza con cui un file viene salvato automaticamente nell'editor. Per i file salvati in precedenza, Visual Studio 2017 salva una copia del file in *%USERPROFILE%\Documents\Visual Studio [versione] \backup files \\ [NomeProgetto]*. Se il file è nuovo e non è ancora stato salvato, Visual Studio lo salva automaticamente usando un nome file generato in modo casuale.

::: moniker-end

**Mantieni informazioni di salvataggio automatico per [n] giorni**

Usare questa opzione per specificare per quanto tempo i file creati per il salvataggio automatico devono restare memorizzati in Visual Studio.

### <a name="see-also"></a>Vedere anche

- [Opzioni (finestra di dialogo)](../../ide/reference/options-dialog-box-visual-studio.md)
