---
title: Dettagli del runtime del controllo del codice sorgente | Microsoft Docs
description: Informazioni su come viene aggiunto un progetto al controllo del codice sorgente, quando un utente aggiunge un file al progetto nel controllo del codice sorgente o tramite un controller di automazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 081e4b75644b51539327083b5e51be5f715507b126a59934a429a80cd0cfdd39
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414363"
---
# <a name="source-control-runtime-details"></a>Dettagli di runtime del controllo del codice sorgente
Un progetto viene aggiunto al controllo del codice sorgente quando l'utente aggiunge un file nel progetto al controllo del codice sorgente o tramite un controller di automazione, ad esempio una procedura guidata. Un progetto non specifica per se stesso che si trova nel controllo del codice sorgente; supporta il controllo del codice sorgente, ma deve essere aggiunto manualmente.

## <a name="registering-with-a-source-control-package"></a>Registrazione con un pacchetto di controllo del codice sorgente
 Quando un file nel progetto viene aggiunto al controllo del codice sorgente, l'ambiente chiama per fornire quattro stringhe opache usate come cookie dal sistema <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> di controllo del codice sorgente. Archiviare queste stringhe nel file di progetto. Queste stringhe devono essere passate al stub del controllo del codice sorgente (il componente Visual Studio che gestisce i pacchetti di controllo del codice sorgente) all'avvio del tipo di progetto chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A> . Questo a sua volta carica il pacchetto di controllo del codice sorgente appropriato e inoltra la chiamata alla relativa implementazione di `IVsSccManager2::RegisterSccProject` .

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>
- [Supporto del controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)
