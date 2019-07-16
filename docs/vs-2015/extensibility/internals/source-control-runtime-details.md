---
title: Dettagli di Runtime del controllo di origine | Microsoft Docs
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68183373"
---
# <a name="source-control-runtime-details"></a>Dettagli di runtime del controllo del codice sorgente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quando l'utente aggiunge un file nel progetto di controllo del codice sorgente o tramite un controller di automazione, ad esempio una procedura guidata, viene aggiunto un progetto al controllo del codice sorgente. Un progetto non è specificata per se stesso che è sotto controllo del codice sorgente; supporta controllo del codice sorgente, ma devono essere aggiunti manualmente a esso.  
  
## <a name="registering-with-a-source-control-package"></a>La registrazione con un pacchetto controllo del codice sorgente  
 Quando un file nel progetto viene aggiunto al controllo del codice sorgente, l'ambiente chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> che consentono di quattro stringhe opache utilizzate come i cookie dal sistema di controllo di origine. Store queste stringhe nel file di progetto. Queste stringhe devono essere passate allo Stub di controllo di origine (il componente di Visual Studio che consente di gestire i pacchetti del controllo origine) all'avvio del tipo di progetto chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>. Ciò a sua volta carica il pacchetto del controllo origine appropriato e inoltra la chiamata alla relativa implementazione di `IVsSccManager2::RegisterSccProject`.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [Supporto del controllo del codice sorgente](../../extensibility/internals/supporting-source-control.md)
