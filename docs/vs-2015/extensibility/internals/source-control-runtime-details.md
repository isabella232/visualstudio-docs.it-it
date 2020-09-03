---
title: Dettagli runtime controllo del codice sorgente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bb52770557fa37a14040b686dcdfbf345a713a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183373"
---
# <a name="source-control-runtime-details"></a>Dettagli di runtime del controllo del codice sorgente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un progetto viene aggiunto al controllo del codice sorgente quando l'utente aggiunge un file nel progetto al controllo del codice sorgente o tramite un controller di automazione, ad esempio una procedura guidata. Un progetto non specifica per se stesso che è sotto il controllo del codice sorgente. supporta il controllo del codice sorgente, ma deve essere aggiunto manualmente.  
  
## <a name="registering-with-a-source-control-package"></a>Registrazione con un pacchetto di controllo del codice sorgente  
 Quando un file nel progetto viene aggiunto al controllo del codice sorgente, l'ambiente chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> per fornire quattro stringhe opache utilizzate come cookie dal sistema di controllo del codice sorgente. Archiviare queste stringhe nel file di progetto. Queste stringhe devono essere passate allo stub del controllo del codice sorgente (il componente di Visual Studio che gestisce i pacchetti del controllo del codice sorgente) all'avvio del tipo di progetto chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A> . Questo, a sua volta, carica il pacchetto del controllo del codice sorgente appropriato e ne invia la chiamata all'implementazione di `IVsSccManager2::RegisterSccProject` .  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [Supporto del controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)
