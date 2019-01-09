---
title: Riferimento (acquisizione a livello di codice) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 826b399aa0ad0b5a45bc6fd80eb73b555cb3f01c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53836356"
---
# <a name="reference-programmatic-capture"></a>Riferimento (acquisizione a livello di codice)
Diagnostica grafica supporta il controllo a livello di programmazione sulle funzionalità di acquisizione, tramite l'API di acquisizione a livello di programmazione. È possibile utilizzare questa API per attivare o disattivare e aggiungere messaggi alla diagnostica grafica HUD (Head-Up Display), inizializzare e creare file di log di grafica e acquisire informazioni grafiche.  

## <a name="programmatic-capture-apis"></a>API di acquisizione a livello di programmazione  

### <a name="classes"></a>Classi  

|nome|Description|  
|----------|-----------------|  
|[VsgDbg Class](vsgdbg-class.md)|Rappresenta l'interfaccia attraverso cui il componente in-app di diagnostica della grafica è controllato a livello di programmazione.|  

### <a name="preprocessor-symbols"></a>Simboli del preprocessore  

|nome|Description|  
|----------|-----------------|  
|[DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)|Quando presente, definisce se il file di log di grafica viene salvato nella directory dei file temporanei dell'utente.|  
|[VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)|Definisce il nome file predefinito del file di log di grafica.|  
|[VSG_NODEFAULT_INSTANCE](vsg-nodefault-instance.md)|Quando presente, definisce se viene fornita un'istanza predefinita della classe `VsgDbg`.|  

## <a name="related-articles"></a>Articoli correlati  

| Titolo | Description |
| - | - |
| [Capturing Graphics Information](capturing-graphics-information.md) | Viene indicato come acquisire informazioni grafiche dall'app basata su DirectX per poter usare gli strumenti di diagnostica della grafica [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per diagnosticare problemi di rendering. |
| [Panoramica](overview-of-visual-studio-graphics-diagnostics.md) | Viene indicato come la diagnostica della grafica consente di eseguire il debug degli errori di rendering nei giochi e nelle app DirectX. |
