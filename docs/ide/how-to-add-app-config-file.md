---
title: 'Procedura: Aggiungere un file app.config a un progetto'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d7e760d952d03a31fdb633ae57c0fb670b50fcc2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62547910"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Procedura: Aggiungere un file di configurazione dell'applicazione a un progetto C#

Aggiungendo un file di configurazione dell'applicazione (file *app.config*) a un progetto C#, è possibile personalizzare il modo in cui CLR individua e carica i file di assembly. Per altre informazioni sui file di configurazione dell'applicazione, vedere [Come il runtime individua gli assembly (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

> [!NOTE]
> Le app UWP non contengono un file *app.config*.

Quando si compila il progetto, l'ambiente di sviluppo copia automaticamente il file *app.config*, modifica il nome di file della copia in modo che corrisponda all'eseguibile, quindi sposta la copia nella directory **bin**.

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Per aggiungere un file di configurazione dell'applicazione a un progetto C#

1. Nella barra dei menu scegliere **Progetto** > **Aggiungi nuovo elemento**.

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento**.

1. Espandere **Installati** > **Elementi di Visual C#** e quindi scegliere il modello **File di configurazione dell'applicazione**.

1. Nella casella di testo **Nome** immettere un nome e quindi scegliere il pulsante **Aggiungi**.

     Un file denominato *app. config* viene aggiunto al progetto.

## <a name="see-also"></a>Vedere anche

- [Gestire le impostazioni dell'applicazione (.NET)](../ide/managing-application-settings-dotnet.md)
- [Schema del file di configurazione (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)
- [Configurazione di app (.NET Framework)](/dotnet/framework/configure-apps/index)