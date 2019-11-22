---
title: Pacchetti VSPackage e Framework di pacchetto gestito | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- managed package framework
- VSPackages, managed package framework
- managed VSPackages, managed package framework
ms.assetid: e8d80e0f-6b5b-4baf-a7df-59fd808c60cd
caps.latest.revision: 16
manager: jillfra
ms.openlocfilehash: 84fb41bfc80415535ca41d6b1a8c9dcf47124c7a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298236"
---
# <a name="vspackages-and-the-managed-package-framework"></a>Pacchetti VSPackage e framework del pacchetto gestito
È possibile ridurre i tempi di sviluppo creando un pacchetto VSPackage con le classi del Framework di pacchetto gestito (MPF) anziché usando le classi di interoperabilità COM.  
  
 Esistono due modi per creare un pacchetto VSPackage gestito:  
  
- Usare il modello di progetto del pacchetto [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
     Per altre informazioni, vedere [procedura dettagliata: creazione di un comando di menu tramite il modello di pacchetto di Visual Studio](https://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de).  
  
- Compilare il pacchetto VSPackage senza il modello di progetto del pacchetto [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
     Ad esempio, è possibile copiare un pacchetto VSPackage di esempio e modificare i GUID e i nomi. 
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Classi del framework di pacchetto gestito](../misc/managed-package-framework-classes.md)  
 Vengono descritti ed elencati gli spazi dei nomi e i file DLL della classe MPF.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Procedura dettagliata: creazione di un comando di menu tramite il modello di pacchetto di Visual Studio](https://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de)  
 Viene illustrato come creare un pacchetto VSPackage gestito.  
  
 [VSPackage gestiti](../misc/managed-vspackages.md)  
 Introduce gli aspetti dei pacchetti VSPackage applicabili al codice gestito.