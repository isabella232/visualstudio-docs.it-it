---
title: Visualizzare dati di esempio in un'interfaccia utente XAML
titleSuffix: Blend for Visual Studio
ms.date: 03/06/2018
ms.topic: conceptual
ms.assetid: 87d31b6c-4607-4121-bb7d-cfc80390ab93
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0614552bbbadd9a472e0780db6f277d423446966
ms.sourcegitcommit: aa302af53de342e75793bd05b10325939dc69b53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2020
ms.locfileid: "75886454"
---
# <a name="display-data-in-blend-for-visual-studio"></a>Visualizzare dati in Blend per Visual Studio

È possibile visualizzare dati di esempio nella finestra di progettazione durante la personalizzazione del layout delle pagine. È possibile generare dati di esempio da zero o usando una classe esistente. È inoltre possibile connettersi a *dati dinamici* che vengono visualizzati nell'app durante l'esecuzione.

> [!NOTE]
> Il pannello **dati** in Blend è supportato solo per i progetti destinati a .NET Framework. Non è supportato per progetti UWP o progetti destinati a .NET Core. 

## <a name="generate-sample-data"></a>Generare dati di esempio

Per generare dati di esempio, aprire un documento XAML. Nel pannello **dati** scegliere l'icona **Crea dati di esempio** ![crea dati di esempio](../designers/media/30540d76-7256-43ce-b5d9-4b2edf3d339f.png) pulsante, quindi scegliere **nuovi dati di esempio**.

Definire la struttura dei dati nel pannello **Dati** e quindi associarla agli elementi dell'interfaccia utente in qualsiasi pagina.

![Pannello Dati](../designers/media/496d7ebc-fe46-42f6-95a8-57b0e5be5d49.png)

Se si vuole che i dati di esempio vengano visualizzati nelle pagine quando si esegue l'app, scegliere **Opzioni origine dati** ![icona Opzioni origine dati](../designers/media/ae1fd260-4f84-420d-b196-45fde357d81d.png), quindi scegliere **Abilita durante l'esecuzione dell'applicazione**.

![Voce di menu Abilita quando l'applicazione è in esecuzione](../designers/media/05d5356d-91bb-4e6b-b3f7-29b76852c4b3.png)

**Breve video:** ![icona riproduci](../designers/media/bldadminconsoleinitialconfigicon.PNG) [creare dati di esempio da zero](https://www.bing.com/videos/search?q=blend%20data&qs=n&form=QBVR&pq=blend%20data&sc=8-7&sp=-1&sk=#view=detail&mid=F8F2449A76956D480FD2F8F2449A76956D480FD2).

## <a name="generate-sample-data-from-a-class"></a>Generare dati di esempio da una classe

Se sono già state create classi che descrivono la struttura dei dati, è possibile usarle per generare dati di esempio.

Per generare dati di esempio da una classe, aprire un documento XAML e quindi nel pannello **dati** fare clic sull'icona **Crea** dati di esempio ![crea dati di esempio](../designers/media/30540d76-7256-43ce-b5d9-4b2edf3d339f.png) pulsante e quindi fare clic su **Crea dati di esempio da classe**.

**Guarda un breve video:** ![icona di riproduzione](../designers/media/bldadminconsoleinitialconfigicon.PNG) [combinare alcune data binding con Blend](https://www.youtube.com/watch?v=LSwPB6CAvjg).

## <a name="see-also"></a>Vedere anche

- [Creare un'interfaccia utente usando Blend per Visual Studio](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md)
