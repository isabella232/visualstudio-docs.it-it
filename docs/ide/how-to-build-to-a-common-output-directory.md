---
title: 'Procedura: Compilare in una directory di output comune'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- output directory
- builds [Visual Studio], common directory
- common directory
ms.assetid: 1fcc2c48-07cb-4c4f-9556-36945e7dfc4e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 12f45890224684ff2e4c411875ab61bdfb698cfb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31942045"
---
# <a name="how-to-build-to-a-common-output-directory"></a>Procedura: Compilare in una directory di output comune

Per impostazione predefinita, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] compila ogni progetto in una soluzione nella relativa cartella all'interno della soluzione. È possibile modificare i percorsi di output di compilazione dei progetti per inserire tutti gli output nella stessa cartella.

## <a name="to-place-all-solution-outputs-in-a-common-directory"></a>Per inserire tutti gli output della soluzione in una directory comune

1.  Fare clic su un progetto nella soluzione.

2.  Scegliere **Proprietà** dal menu **Progetto**.

3.  A seconda del tipo di progetto, fare clic sulla scheda **Compila** o **Build** e impostare il **Percorso di output** su una cartella da usare per tutti i progetti della soluzione.

4.  Ripetere i passaggi da 1 a 3 per tutti i progetti della soluzione.

## <a name="see-also"></a>Vedere anche

- [Compilare](../ide/compiling-and-building-in-visual-studio.md)
- [Procedura: modificare la directory dell'output compilato](../ide/how-to-change-the-build-output-directory.md)