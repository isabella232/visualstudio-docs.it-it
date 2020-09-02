---
title: "Procedura: aggiungere un file di configurazione dell'applicazione a un progetto C# | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f8417b5520dc9587fa3231a3bc459335d2a9896d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667525"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Procedura: aggiungere un file di configurazione dell'applicazione a un progetto C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aggiungendo un file di configurazione dell'applicazione (file app.config) a un progetto C#, è possibile personalizzare il modo in cui CLR individua e carica i file di assembly. Per ulteriori informazioni sui file di configurazione dell'applicazione, vedere [come il runtime individua gli assembly](https://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34).

> [!NOTE]
> Windows Store non supporta <xref:System.Configuration> . Di conseguenza, le app dello Store non contengono un modello di app.config.

 Quando si compila il progetto, l'ambiente di sviluppo copia automaticamente il file app.config, modifica il nome di file della copia in modo che corrisponda all'eseguibile, quindi sposta la copia nella directory bin.

### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>Per aggiungere un file di configurazione dell'applicazione al progetto C#

1. Sulla barra dei menu scegliere **progetto**, **Aggiungi nuovo elemento**.

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento** .

2. Espandere **installato**, espandere **elementi Visual C#**, quindi scegliere il modello **file di configurazione dell'applicazione** .

3. Nella casella di testo **Nome** immettere un nome e quindi scegliere il pulsante **Aggiungi**.

     Un file denominato app.config viene aggiunto al progetto.

## <a name="see-also"></a>Vedere anche
 Gestione [dello schema del file di configurazione](https://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38) [delle impostazioni dell'applicazione (.NET)](../ide/managing-application-settings-dotnet.md) [configurazione](https://msdn.microsoft.com/library/86bd26d3-737e-4484-9782-19b17f34cd1f) delle app [procedura: configurare un'App per la destinazione di una versione .NET Framework](https://msdn.microsoft.com/5247b307-89ca-417b-8dd0-e8f9bd2f4717) [usando l'ambiente di sviluppo di Visual Studio per C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)