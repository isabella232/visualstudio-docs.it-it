---
title: 'Dettagli del runtime del controllo del codice sorgente : Documenti Microsoft'
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
ms.openlocfilehash: 92ce5e822ec7360b3b1a4010d250a4349443c142
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705044"
---
# <a name="source-control-runtime-details"></a>Dettagli di runtime del controllo del codice sorgente
Un progetto viene aggiunto al controllo del codice sorgente quando l'utente aggiunge un file nel progetto al controllo del codice sorgente o tramite un controller di automazione, ad esempio una procedura guidata. Un progetto non specifica per se stesso che è sotto controllo del codice sorgente; supporta il controllo del codice sorgente, ma deve essere aggiunto manualmente.

## <a name="registering-with-a-source-control-package"></a>Registrazione con un pacchetto del controllo del codice sorgenteRegistering with a Source Control Package
 Quando un file nel progetto viene aggiunto al <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> controllo del codice sorgente, l'ambiente chiama per fornire quattro stringhe opache che vengono utilizzate come cookie dal sistema di controllo del codice sorgente. Archiviare queste stringhe nel file di progetto. Queste stringhe devono essere passate allo Stub del controllo del codice sorgente (il componente <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>di Visual Studio che gestisce i pacchetti del controllo del codice sorgente) all'avvio del tipo di progetto chiamando . Questo a sua volta carica il pacchetto del controllo `IVsSccManager2::RegisterSccProject`del codice sorgente appropriato e inoltra la chiamata all'implementazione di .

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>
- [Supporto del controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)
