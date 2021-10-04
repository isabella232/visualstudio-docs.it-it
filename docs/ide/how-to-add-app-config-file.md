---
title: 'Procedura: Aggiungere un file app.config a un progetto'
description: Informazioni su come aggiungere un file app.config a un progetto C# per poter personalizzare il modo in cui Common Language Runtime individua e carica i file di assembly.
ms.custom: SEO-VS-2020
ms.date: 11/20/2020
ms.topic: how-to
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: 6c063aa1dbea8a9953bc3c9e44cf72de5514e0f8
ms.sourcegitcommit: 541871db9065c4fb1b21c24f980c563991b183c7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2021
ms.locfileid: "129431627"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Procedura: Aggiungere un file di configurazione dell'applicazione a un progetto C#

Aggiungendo un file di configurazione dell'applicazione (file *app.config*) a un progetto C#, è possibile personalizzare il modo in cui CLR individua e carica i file di assembly. Per altre informazioni sui file di configurazione dell'applicazione, vedere [Come il runtime individua gli assembly (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

> [!NOTE]
> Le app UWP non contengono un file *app.config*.

Quando si compila il progetto, l'ambiente di sviluppo copia automaticamente il file *app.config*, modifica il nome di file della copia in modo che corrisponda all'eseguibile, quindi sposta la copia nella directory **bin**.

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Per aggiungere un file di configurazione dell'applicazione a un progetto C#

1. Nella barra dei menu scegliere **Project**  >  **Aggiungi nuovo elemento**.

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento** .

1. Espandere **Elementi**  >  **di Visual C# installati** e quindi scegliere il modello File di configurazione **dell'applicazione.**

1. Nella casella di testo **Nome** immettere un nome e quindi scegliere il pulsante **Aggiungi**.

     Un file denominato *app. config* viene aggiunto al progetto.

## <a name="see-also"></a>Vedi anche

- [Gestire le impostazioni dell'applicazione (.NET)](../ide/managing-application-settings-dotnet.md)
- [Schema del file di configurazione (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)
- [Configurazione di app (.NET Framework)](/dotnet/framework/configure-apps/index)
