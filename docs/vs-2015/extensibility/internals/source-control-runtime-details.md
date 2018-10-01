---
title: Dettagli di Runtime del controllo di origine | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ca2d6830a9feb61c088274761995eeb227b1d661
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529939"
---
# <a name="source-control-runtime-details"></a>Dettagli di runtime del controllo del codice sorgente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [dettagli di Runtime del controllo sorgente](https://docs.microsoft.com/visualstudio/extensibility/internals/source-control-runtime-details).  
  
Quando l'utente aggiunge un file nel progetto di controllo del codice sorgente o tramite un controller di automazione, ad esempio una procedura guidata, viene aggiunto un progetto al controllo del codice sorgente. Un progetto non è specificata per se stesso che è sotto controllo del codice sorgente; supporta controllo del codice sorgente, ma devono essere aggiunti manualmente a esso.  
  
## <a name="registering-with-a-source-control-package"></a>La registrazione con un pacchetto controllo del codice sorgente  
 Quando un file nel progetto viene aggiunto al controllo del codice sorgente, l'ambiente chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> che consentono di quattro stringhe opache utilizzate come i cookie dal sistema di controllo di origine. Store queste stringhe nel file di progetto. Queste stringhe devono essere passate allo Stub di controllo di origine (il componente di Visual Studio che consente di gestire i pacchetti del controllo origine) all'avvio del tipo di progetto chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>. Ciò a sua volta carica il pacchetto del controllo origine appropriato e inoltra la chiamata alla relativa implementazione di `IVsSccManager2::RegisterSccProject`.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [Supporto del controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)

