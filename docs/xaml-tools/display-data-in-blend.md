---
title: Visualizzare dati di esempio in un'interfaccia utente XAML
titleSuffix: Blend for Visual Studio
description: Informazioni su come generare dati di esempio da zero o da una classe esistente in Blend per Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 03/06/2018
ms.topic: conceptual
ms.assetid: 87d31b6c-4607-4121-bb7d-cfc80390ab93
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.workload:
- multiple
ms.openlocfilehash: e359ad5cd4d7272661fbddb6bce263d7a7c6c202
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710551"
---
# <a name="display-data-in-blend-for-visual-studio"></a>Visualizzare dati in Blend per Visual Studio

È possibile visualizzare dati di esempio nella finestra di progettazione durante la personalizzazione del layout delle pagine. È possibile generare dati di esempio da zero o usando una classe esistente. È inoltre possibile connettersi a *dati dinamici* che vengono visualizzati nell'app durante l'esecuzione.

> [!NOTE]
> Il **pannello Dati** in Blend è supportato solo per i progetti che hanno come destinazione .NET Framework. Non è supportato per i progetti UWP o i progetti che hanno come destinazione .NET Core.

## <a name="generate-sample-data"></a>Generare i dati di esempio

Per generare dati di esempio, aprire un documento XAML. Nel pannello **Dati** scegliere il pulsante Crea dati **di esempio** Crea dati di esempio e quindi scegliere Nuovi dati ![ di ](../designers/media/30540d76-7256-43ce-b5d9-4b2edf3d339f.png) **esempio**.

Definire la struttura dei dati nel pannello **Dati** e quindi associarla agli elementi dell'interfaccia utente in qualsiasi pagina.

![Pannello Dati](../designers/media/496d7ebc-fe46-42f6-95a8-57b0e5be5d49.png)

Se si vuole che i dati di esempio vengano  visualizzati nelle pagine quando si esegue l'app, scegliere Opzioni origine dati Icona Opzioni origine dati e quindi scegliere Abilita durante ![ ](../designers/media/ae1fd260-4f84-420d-b196-45fde357d81d.png) l'esecuzione **dell'applicazione**.

![Voce di menu Abilita quando l'applicazione è in esecuzione](../designers/media/05d5356d-91bb-4e6b-b3f7-29b76852c4b3.png)

**Guardare un breve video:** ![ Icona ](../designers/media/bldadminconsoleinitialconfigicon.PNG) [Riproduci Crea dati di esempio da zero.](https://www.bing.com/videos/search?q=blend%20data&qs=n&form=QBVR&pq=blend%20data&sc=8-7&sp=-1&sk=#view=detail&mid=F8F2449A76956D480FD2F8F2449A76956D480FD2&preserve-view=true)

## <a name="generate-sample-data-from-a-class"></a>Generare dati di esempio da una classe

Se sono già state create classi che descrivono la struttura dei dati, è possibile usarle per generare dati di esempio.

Per generare dati di esempio da una classe,  aprire un documento  XAML e quindi nel pannello Dati fare clic sul pulsante Crea dati di esempio Crea dati di esempio e quindi su Crea dati di esempio ![ dalla ](../designers/media/30540d76-7256-43ce-b5d9-4b2edf3d339f.png) **classe**.

**Guardare un breve video:** ![ Icona Di ](../designers/media/bldadminconsoleinitialconfigicon.PNG) [riproduzione Mix up some data binding with Blend](https://www.youtube.com/watch?v=LSwPB6CAvjg).

## <a name="see-also"></a>Vedi anche

- [Creare un'interfaccia utente usando Blend per Visual Studio](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md)