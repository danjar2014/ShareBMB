$folderPath = 'filesystem::\\frmdfs1\eu_digital_working$\ImportCISCMPP'
$csvin = Get-ChildItem -Path $folderPath -Filter *.csv | Sort-Object CreationTime

foreach ($file in $csvin) {
    Write-Host "Traitement de fichier : $($file.Name)"

    try {
        if (-not (Test-Path -Path $file.FullName -PathType Leaf)) {
            Write-Warning "$($file.Name) not found"
        } else {
            Write-Host "$($file.Name) existe, on continue"
            # Traitement à ajouter ici
        }
    } catch {
        Write-Warning "Erreur pendant le traitement de $($file.Name) : $_"
    }
}
