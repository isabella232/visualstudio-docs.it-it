---
title: Dettagli runtime controllo del codice sorgente | Microsoft Docs
description: Informazioni sul modo in cui un progetto viene aggiunto al controllo del codice sorgente, quando un utente aggiunge un file al progetto nel controllo del codice sorgente o tramite un controller di automazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbe1e0e915a28412fcfd411e72b6d622e065b8f8
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877975"
---
# <a name="source-control-runtime-details"></a>Dettagli di runtime del controllo del codice sorgente
Un progetto viene aggiunto al controllo del codice sorgente quando l'utente aggiunge un file nel progetto al controllo del codice sorgente o tramite un controller di automazione, ad esempio una procedura guidata. Un progetto non specifica per se stesso che è sotto il controllo del codice sorgente. supporta il controllo del codice sorgente, ma deve essere aggiunto manualmente.

## <a name="registering-with-a-source-control-package"></a>Registrazione con un pacchetto di controllo del codice sorgente
 Quando un file nel progetto viene aggiunto al controllo del codice sorgente, l'ambiente chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> per fornire quattro stringhe opache utilizzate come cookie dal sistema di controllo del codice sorgente. Archiviare queste stringhe nel file di progetto. Queste stringhe devono essere passate allo stub del controllo del codice sorgente (il componente di Visual Studio che gestisce i pacchetti del controllo del codice sorgente) all'avvio del tipo di progetto chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A> . Questo, a sua volta, carica il pacchetto del controllo del codice sorgente appropriato e ne invia la chiamata all'implementazione di `IVsSccManager2::RegisterSccProject` .

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>
- [Supporto del controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)
