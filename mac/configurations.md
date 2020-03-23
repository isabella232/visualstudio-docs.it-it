---
title: Informazioni sulle configurazioni della build
description: Questo articolo descrive le varie configurazioni della build disponibili in Visual Studio per Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: d1511434a34017a7f0f7da65fe1ea6956d45d497
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "71128408"
---
# <a name="understanding-build-configurations"></a>Informazioni sulle configurazioni della build

È possibile archiviare diverse configurazioni delle proprietà della soluzione e del progetto da usare in diversi tipi di compilazioni durante il processo di sviluppo. I progetti creati da Visual Studio per Mac usando un modello includono in genere le configurazioni debug e rilascio che supportano rispettivamente il debug di un'app e la distribuzione di un'app. 

Se si desidera creare configurazioni personalizzate, vedere [Creazione e modifica di configurazioni](/visualstudio/mac/create-and-edit-configurations)di build .

>[!NOTE]
>Questo argomento si applica a Visual Studio per Mac. Per Visual Studio in Windows, vedere [Informazioni sulle configurazioni](/visualstudio/ide/understanding-build-configurations)di compilazione .

## <a name="solution-configurations"></a>Configurazioni di soluzioni

Le configurazioni di soluzione vengono utilizzate per specificare le configurazioni per tutti i progetti in una soluzione. Utilizzando la scheda Mapping di configurazione nell'elemento **Compila > configurazioni,** è possibile assegnare una configurazione di destinazione per ogni elemento nella soluzione aperta. **Configuration Mappings** Ciò è dimostrato nell'immagine seguente:This is demonstrated in the following image:

![Opzioni di Mapping di configurazione](media/projects-and-solutions-image3.png)

Per altre informazioni sulle configurazioni, vedere il video di James Montemagno su [Configuration Manager](https://www.youtube.com/watch?v=tjSdkqYh5Vg).

## <a name="project-build-configurations"></a>Configurazioni della build di progetti

I progetti tendono ad avere più configurazioni. La configurazione e la piattaforma di una destinazione di progetto vengono utilizzate insieme per specificare le proprietà da usare quando viene compilato. Il passaggio da una configurazione all'altra consente output diversi in fase di compilazione. Con una configurazione di debug, ad esempio, l'output includerà simboli di debug che consentono al debugger di risolvere i nomi delle funzioni, dei parametri o delle variabili dall'analisi dello stack di un'applicazione bloccata. Anche se queste informazioni aggiuntive sono utili durante lo sviluppo, comportano dimensioni molto maggiori dei file e non sono ideale per la distribuzione.

Ogni piattaforma ha una configurazione specifica per la compilazione. È possibile accedere alle pagine di configurazione della compilazione per i progetti passando alla sezione **Compilazione** nella finestra di dialogo **Opzioni progetto.** Aprire questa finestra di dialogo facendo clic con il pulsante destro del mouse sul progetto e selezionando **Opzioni** oppure facendo doppio clic sul progetto in Esplora soluzioni.

## <a name="run-configuration"></a>Configurazione di esecuzione

Visual Studio per Mac consente di impostare una _configurazione di esecuzione._ Le configurazioni di esecuzione sono disponibili in un elenco a discesa sulla barra degli strumenti accanto al selettore della configurazione della build, come illustrato di seguito:

![Elenco a discesa della configurazione di esecuzione](media/projects-and-solutions-image8.png)

Una configurazione di esecuzione è un set di opzioni di esecuzione con un nome. Per un progetto possono essere definite diverse configurazioni per scopi diversi. Le configurazioni di esecuzione vengono definite a livello di progetto e verrà creato automaticamente un valore predefinito per ogni progetto eseguibile, anche se è possibile aggiungerne il numero necessario. Alcuni tipi di progetto generano automaticamente altre configurazioni di esecuzione. Ad esempio, i progetti watchOS possono generare _configurazioni Glance e Notification.For example,_ watchOS projects may generate Glance and Notification configurations.

Le configurazioni possono essere condivise con altri sviluppatori (nel qual caso le configurazioni verranno archiviate nel file con estensione csproj) o mantenute localmente (nel qual caso verranno archiviate in un file con estensione user).

### <a name="android-run-configurations"></a>Configurazioni di esecuzione Android

Le configurazioni di esecuzione per i progetti Android consentono l'avvio delle configurazioni per i progetti Android durante l'esecuzione o il debug del progetto. È possibile passare dati aggiuntivi di finalità e impostare flag di finalità per testare i componenti in condizioni di avvio diverse.

Alle attività diverse da `MainLauncher` è necessario aggiungere `Exported=true` all'attributo Activity per il debug su un dispositivo fisico o definire filtri di intent.

## <a name="examples-of-data-that-might-be-included-in-run-configurations"></a>Esempi di dati che possono essere inclusi nelle configurazioni di esecuzione

L'elenco seguente offre alcuni esempi di dati che possono essere inclusi nelle configurazioni di esecuzione:

* Progetto .NET normale
  * App di avvio alternativa
  * Argomenti di avvio
  * Directory di lavoro
  * Variabili di ambiente
  * Opzioni di runtime di Mono (da usare solo se in esecuzione in Mono)
* Progetto Android
  * Punto di ingresso (attività, servizio, ricevitore)
  * Argomenti e dati di intent
* Progetto iOS
  * Modalità (normale, recupero in background)
* Progetto di estensione iOS
  * App di avvio: predefinita o personalizzata
* Progetto WatchKit
  * Modalità (Glance, notifica)
  * Payload di notifica

## <a name="see-also"></a>Vedere anche

- [Informazioni sulle configurazioni della build (Visual Studio in Windows)](/visualstudio/ide/understanding-build-configurations)
