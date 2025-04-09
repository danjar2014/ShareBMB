# Dossier contenant les fichiers CSV
$folderPath = "C:\Ton\Chemin\Ici"

# Récupère les fichiers CSV triés par date de création croissante
$csvFiles = Get-ChildItem -Path $folderPath -Filter *.csv | Sort-Object CreationTime

foreach ($file in $csvFiles) {
    Write-Host "Traitement du fichier : $($file.Name)"

    try {
        # Lis le contenu du fichier CSV
        $data = Import-Csv -Path $file.FullName

        # ----- TON BLOC DE TRAITEMENT ICI -----
        # Exemple : afficher le nombre de lignes
        Write-Host "Nombre de lignes : $($data.Count)"

        # --------------------------------------

        # Suppression du fichier après traitement
        Remove-Item -Path $file.FullName -Force
        Write-Host "Fichier supprimé : $($file.Name)"
    }
    catch {
        Write-Warning "Erreur pendant le traitement de $($file.Name) : $_"
    }
}
