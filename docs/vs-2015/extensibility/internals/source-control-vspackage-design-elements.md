---
title: Elementi di progettazione VSPackage del controllo del codice sorgente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 06cd4523f91c341029140764b31fbd0ee262d551
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155690"
---
# <a name="source-control-vspackage-design-elements"></a>Elementi di progettazione dei pacchetti VSPackage di controllo del codice sorgente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Negli argomenti di questa sezione viene illustrata la struttura che il pacchetto VSPackage del controllo del codice sorgente deve implementare per l'integrazione completa. Elenca inoltre le interfacce e i servizi che possono essere implementati dal pacchetto VSPackage del controllo del codice sorgente e le interfacce e i servizi che il pacchetto VSPackage del controllo del codice sorgente può utilizzare da altri [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] componenti per supportare il modello e la funzionalità del controllo del codice sorgente  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Struttura VSPackage](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)  
 Definisce la struttura del pacchetto VSPackage del controllo del codice sorgente.  
  
 [Interfacce e servizi correlati](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)  
 Elenca i servizi e le interfacce correlate al pacchetto del controllo del codice sorgente.  
  
 [Servizi forniti](../../extensibility/internals/services-provided-source-control-vspackage.md)  
 Descrive il servizio di controllo del codice sorgente fornito dal pacchetto VSPackage del controllo del codice sorgente.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Creazione di un pacchetto VSPackage di controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md)  
 Viene illustrato come creare un VSPackage del controllo del codice sorgente che non solo fornisce la funzionalità del controllo del codice sorgente, ma può essere utilizzato per personalizzare l' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interfaccia utente del controllo del codice sorgente
