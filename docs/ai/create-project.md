---
title: Creare un progetto AI da un modello
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 759ee562e5d3648cf831c6a1247bc660596336a1
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638595"
---
# <a name="create-an-ai-project-from-a-template-in-visual-studio"></a>Creare un progetto AI da un modello in Visual Studio

Dopo aver [installato Visual Studio Tools for AI](installation.md) è facile creare un nuovo progetto AI usando vari modelli.

1. Avviare Visual Studio.

2. Selezionare **File > Nuovo > progetto** (Ctrl+Shift+N). Nel finestra di dialogo **Nuovo progetto** cercare "**AI Tools**" (Strumenti AI) e selezionare il modello desiderato. Si noti che la selezione di un modello visualizza una breve descrizione di ciò che offre tale modello.

    ![Finestra di dialogo VS2017 Nuovo progetto con modelli Python](media/create-project/new-ai-project.png)

3. Per questa Guida rapida, selezionare il modello "**TensorFlow Application**" (Applicazione TensorFlow), assegnare al progetto un nome (ad esempio, "MNIST") e un percorso e selezionare **OK**.

4. Visual Studio crea il file di progetto (un file `.pyproj` su disco) insieme a qualsiasi altro file, come descritto nel modello. Con il modello "TensorFlow Application", il progetto contiene un file con lo stesso nome del progetto. Il file è aperto nell'editor di Visual Studio per impostazione predefinita.

    ![Progetto risultante quando si usa il modello di applicazione Python](media/create-project/new-tensorflowapp.png)

5. Si noti che il codice importa già diverse librerie, tra cui TensorFlow e NumPy, nonché librerie di sistema e del sistema operativo. Avvia inoltre l'applicazione con alcuni argomenti di input per consentire di cambiare facilmente il percorso dei dati di training di input, dei modelli di output e dei file di log. Questi parametri sono utili quando si inviano processi a più contesti di calcolo, ad esempio una directory diversa nell'ambiente di sviluppo locale o una condivisione file di Azure.

6. Per il progetto sono anche state create alcune proprietà che semplificano il debug dell'applicazione passando automaticamente gli argomenti della riga di comando a questi parametri di input. **Fare clic con il pulsante destro del mouse** sul progetto e selezionare **Proprietà**

    ![Proprietà](media/create-project/project-properties.png)

7. Fare clic sulla scheda **Debug** per vedere gli argomenti di script aggiunti automaticamente. È possibile modificarli in base alle proprie esigenze a seconda della posizione dei dati di input e della posizione di archiviazione preferita per i dati di output.

    ![Proprietà](media/create-project//project-properties_1.png)

8. Eseguire il programma premendo Ctrl+F5 o selezionando **Debug > Avvia senza eseguire debug** del menu. I risultati vengono visualizzati nella finestra della console.
