---
title: 'Procedura: Aggiungere un file app.config a un progetto'
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: fe659979cadf4d9e5752f7bbe85150aae848de08
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85770827"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Procedura: Aggiungere un file di configurazione dell'applicazione a un progetto C#

Aggiungendo un file di configurazione dell'applicazione (file *app.config*) a un progetto C#, è possibile personalizzare il modo in cui CLR individua e carica i file di assembly. Per altre informazioni sui file di configurazione dell'applicazione, vedere [Come il runtime individua gli assembly (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

> [!NOTE]
> Le app UWP non contengono un file *app.config*.

Quando si compila il progetto, l'ambiente di sviluppo copia automaticamente il file *app.config*, modifica il nome di file della copia in modo che corrisponda all'eseguibile, quindi sposta la copia nella directory **bin**.

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Per aggiungere un file di configurazione dell'applicazione a un progetto C#

1. Sulla barra dei menu scegliere **progetto**  >  **Aggiungi nuovo elemento**.

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento** .

1. Espandere **Installed**  >  **elementi di Visual C#** installati, quindi scegliere il modello **file di configurazione dell'applicazione** .

1. Nella casella di testo **Nome** immettere un nome e quindi scegliere il pulsante **Aggiungi**.

     Un file denominato *app. config* viene aggiunto al progetto.

## <a name="see-also"></a>Vedere anche

- [Gestire le impostazioni dell'applicazione (.NET)](../ide/managing-application-settings-dotnet.md)
- [Schema del file di configurazione (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)
- [Configurazione di app (.NET Framework)](/dotnet/framework/configure-apps/index)
