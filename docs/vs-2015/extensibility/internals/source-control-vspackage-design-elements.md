---
title: Gli elementi di progettazione dei pacchetti VSPackage di controllo di origine | Microsoft Docs
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
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: efc1133a57db0c179fbac05db9f6472237577e9e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532522"
---
# <a name="source-control-vspackage-design-elements"></a>Elementi di progettazione dei pacchetti VSPackage di controllo del codice sorgente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [gli elementi di progettazione VSPackage di controllo di origine](https://docs.microsoft.com/visualstudio/extensibility/internals/source-control-vspackage-design-elements).  
  
Negli argomenti di questa sezione descrivono la struttura di controllo del codice sorgente pacchetto VSPackage deve implementare per l'integrazione completa. Elenca anche le interfacce e servizi che l'origine pacchetto VSPackage di controllo possono implementare le interfacce e i servizi è possibile usare il controllo del codice sorgente VSPackage dagli altri [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] componenti per supportare la propria origine controllano modello e le funzionalità.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Struttura VSPackage](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)  
 Definisce la struttura del pacchetto VSPackage di controllo del codice sorgente.  
  
 [Interfacce e servizi correlati](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)  
 Elenca le interfacce correlate al pacchetto di controllo sorgente e i servizi.  
  
 [Servizi forniti](../../extensibility/internals/services-provided-source-control-vspackage.md)  
 Descrive il servizio di controllo di origine fornito da VSPackage di controllo del codice sorgente.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Creazione di un pacchetto VSPackage di controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-vspackage.md)  
 Viene illustrato come creare un controllo del codice sorgente VSPackage che non solo fornisce funzionalità di controllo di origine ma può essere usato per personalizzare il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] controllo dell'interfaccia utente del codice sorgente.

