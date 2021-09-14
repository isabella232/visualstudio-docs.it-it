---
title: 'Progettazione pacchetti: aggiungere & funzionalità ed elementi al pacchetto'
titleSuffix: ''
description: Esaminare come aggiungere e rimuovere funzionalità ed elementi in un pacchetto SharePoint usando Progettazione pacchetti in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerDesign
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 946b3fca7e99bf2aaf1395d63f13626f5e5e5859
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625134"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer"></a>Procedura: Aggiungere e rimuovere funzionalità ed elementi a un pacchetto tramite Progettazione pacchetti
  Quando si crea una soluzione SharePoint, Visual Studio le funzionalità SharePoint predefinite al pacchetto nella soluzione. Prima della distribuzione finale, è possibile aggiungere e rimuovere SharePoint di progetto e funzionalità per modificare il SharePoint pacchetto.

 In alternativa, è possibile usare Packaging Explorer per aggiungere e rimuovere SharePoint di progetto. È anche possibile visualizzare e modificare la gerarchia SharePoint elementi di progetto e funzionalità che vengono inseriti nel pacchetto (con estensione wsp). Per altre informazioni, vedere Procedura: Aggiungere e rimuovere funzionalità ed elementi a un pacchetto [tramite Packaging Explorer.](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)

## <a name="add-features-to-a-sharepoint-package"></a>Aggiungere funzionalità a un pacchetto SharePoint distribuzione
 È possibile usare Progettazione pacchetti per aggiungere funzionalità a un SharePoint pacchetto.

#### <a name="to-add-sharepoint-features-with-the-package-designer"></a>Per aggiungere SharePoint funzionalità con Progettazione pacchetti

1. Aprire Progettazione **pacchetti**.

    Per altre informazioni, vedere [Procedura: Personalizzare un pacchetto SharePoint soluzione](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Aggiungere una o più SharePoint funzionalità eseguendo uno o più dei passaggi seguenti:

   1. Fare doppio clic su ogni elemento **nell'elenco Elementi** della soluzione che si vuole aggiungere.

   2. Scegliere un elemento da aggiungere e quindi scegliere il **pulsante** Aggiungi (>).

   3. Scegliere il **pulsante Aggiungi** tutto (>>) per aggiungere tutti gli elementi contemporaneamente.

      Ad esempio, è possibile fare doppio clic su un elemento nell'elenco **Elementi** della soluzione per aggiungerlo all'elenco **Elementi nell'elenco** Pacchetto.

      I SharePoint Project elementi e funzionalità vengono visualizzati **nell'elenco Elementi nell'elenco** Pacchetto.

## <a name="remove-features-from-a-sharepoint-package"></a>Rimuovere funzionalità da un pacchetto SharePoint distribuzione
 È possibile usare Progettazione pacchetti per rimuovere le funzionalità in un SharePoint pacchetto.

#### <a name="to-remove-sharepoint-features-with-the-package-designer"></a>Per rimuovere SharePoint funzionalità con Progettazione pacchetti

1. Nell'elenco Elementi nel pacchetto scegliere un elemento da rimuovere e quindi scegliere il pulsante Rimuovi **(<)** oppure scegliere il pulsante Rimuovi tutto (<<) per rimuovere tutti gli elementi.  

     I SharePoint elementi visualizzati **nell'elenco Elementi nella** soluzione .

## <a name="see-also"></a>Vedi anche
- [Creare SharePoint pacchetti della soluzione](../sharepoint/creating-sharepoint-solution-packages.md)
- [Procedura: Personalizzare un pacchetto SharePoint soluzione](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Procedura: Creare un pacchetto](/previous-versions/ee231585(v=vs.110))