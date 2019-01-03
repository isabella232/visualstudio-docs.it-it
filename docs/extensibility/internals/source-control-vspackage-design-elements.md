---
title: Gli elementi di progettazione dei pacchetti VSPackage di controllo di origine | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f4446bb0cab421e06910ac7f7c5893680c36edf6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53872239"
---
# <a name="source-control-vspackage-design-elements"></a>Elementi di progettazione dei pacchetti VSPackage di controllo del codice sorgente
Negli argomenti di questa sezione descrivono la struttura di controllo del codice sorgente pacchetto VSPackage deve implementare per l'integrazione completa. Elenca anche le interfacce e servizi che l'origine pacchetto VSPackage di controllo possono implementare le interfacce e i servizi è possibile usare il controllo del codice sorgente VSPackage dagli altri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componenti per supportare la propria origine controllano modello e le funzionalità.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Struttura VSPackage](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)  
 Definisce la struttura del pacchetto VSPackage di controllo del codice sorgente.  
  
 [Interfacce e servizi correlati](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)  
 Elenca le interfacce correlate al pacchetto di controllo sorgente e i servizi.  
  
 [Servizi forniti](../../extensibility/internals/services-provided-source-control-vspackage.md)  
 Descrive il servizio di controllo di origine fornito da VSPackage di controllo del codice sorgente.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Creazione di un pacchetto VSPackage di controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md)  
 Viene illustrato come creare un controllo del codice sorgente VSPackage che non solo fornisce funzionalità di controllo di origine ma può essere usato per personalizzare il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] controllo dell'interfaccia utente del codice sorgente.