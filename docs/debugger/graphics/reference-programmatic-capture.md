---
title: Riferimento (acquisizione a livello di codice) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a462d22df9768d2ffc8b344933e9f5c1f556575a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62895521"
---
# <a name="reference-programmatic-capture"></a>Riferimento (acquisizione a livello di codice)
Diagnostica della grafica supporta il controllo a livello di programmazione sulle funzionalità di acquisizione, tramite l'API di acquisizione a livello di programmazione. È possibile utilizzare questa API per attivare o disattivare e aggiungere messaggi alla diagnostica grafica HUD (Head-Up Display), inizializzare e creare file di log di grafica e acquisire informazioni grafiche.

## <a name="programmatic-capture-apis"></a>API di acquisizione a livello di programmazione

### <a name="classes"></a>Classi

|Nome|Descrizione|
|----------|-----------------|
|[VsgDbg Class](vsgdbg-class.md)|Rappresenta l'interfaccia attraverso cui il componente in-app di diagnostica della grafica è controllato a livello di programmazione.|

### <a name="preprocessor-symbols"></a>Simboli del preprocessore

|Nome|Descrizione|
|----------|-----------------|
|[DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)|Quando presente, definisce se il file di log di grafica viene salvato nella directory dei file temporanei dell'utente.|
|[VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)|Definisce il nome file predefinito del file di log di grafica.|
|[VSG_NODEFAULT_INSTANCE](vsg-nodefault-instance.md)|Quando presente, definisce se viene fornita un'istanza predefinita della classe `VsgDbg`.|

## <a name="related-articles"></a>Articoli correlati

| Titolo | Descrizione |
| - | - |
| [Capturing Graphics Information](capturing-graphics-information.md) | Viene indicato come acquisire informazioni grafiche dall'app basata su DirectX per poter usare gli strumenti di diagnostica della grafica [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per diagnosticare problemi di rendering. |
| [Panoramica](overview-of-visual-studio-graphics-diagnostics.md) | Viene indicato come la diagnostica grafica consente di eseguire il debug degli errori di rendering nei giochi e nelle app DirectX. |
