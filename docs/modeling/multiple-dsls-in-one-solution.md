---
title: Più soluzioni DSL in una soluzione unica
description: Informazioni su come creare un pacchetto di più linguaggi specifici di dominio (DSL) come parte di una singola soluzione in modo che siano installati insieme.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: d26d321f93d3d70300c8bdfaa758ec87309840bd8d21db3341a5cf7e2040505d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121231522"
---
# <a name="multiple-dsls-in-one-solution"></a>Più soluzioni DSL in una soluzione unica

È possibile creare un pacchetto di diversi linguaggi specifici di dominio come parte di un'unica soluzione, in modo che vengano installati insieme.

Esistono varie tecniche per integrare più linguaggi specifici di dominio. Per altre informazioni, vedere Integrazione di modelli tramite [Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) e [Procedura: Aggiungere](../modeling/how-to-add-a-drag-and-drop-handler.md) un gestore di trascinamento della selezione e Personalizzazione del [comportamento di copia.](../modeling/customizing-copy-behavior.md)

## <a name="build-more-than-one-dsl-in-the-same-solution"></a>Compilare più DSL nella stessa soluzione

1. Creare un nuovo **progetto Project VSIX.**

2. Creare due o più progetti DSL nella directory della soluzione VSIX.

   - Per ogni linguaggio specifico di dominio, aprire una nuova istanza di Visual Studio. Creare il nuovo linguaggio specifico di dominio e specificare la stessa cartella soluzione della soluzione VSIX.

   - Assicurarsi di creare ogni linguaggio specifico di dominio con un'estensione di file diversa.

   - Modificare i nomi dei **progetti Dsl** e **DslPackage** in modo che siano tutti diversi. Ad esempio: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.

   - In ogni **DslPackage \* \source.extension.tt** aggiornare questa riga con il nome del progetto Dsl corretto:

      `string dslProjectName = "Dsl2";`

   - Nella soluzione VSIX aggiungere i progetti Dsl* e DslPackage. \* Può essere utile inserire ogni coppia in una specifica cartella soluzione.

2. Combinare i manifesti VSIX dei linguaggi specifici di dominio:

   1. Aprire _YourVsixProject_**\source.extension.manifest**.

   2. Per ogni DSL scegliere **Aggiungi contenuto** e aggiungere:

       - `Dsl*` progetto come **componente MEF**

       - `DslPackage*` progetto come **componente MEF**

       - `DslPackage*` progetto come pacchetto **VS**

3. Compilare la soluzione.

   Il progetto VSIX risultante installerà entrambi i linguaggi specifici di dominio. È possibile testarli usando F5 o distribuire _YourVsixProject_**\bin\Debug \\ \* .vsix**.

## <a name="see-also"></a>Vedi anche

- [Integrazione di modelli tramite ModelBus di Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Procedura: Aggiungere un gestore di trascinamento della selezione](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md)