<p align="center">Installation and setup</p>


## Basic installation

You can install this package via composer using:

- composer require spatie/laravel-backup


The package will automatically register its service provider. To publish the config file to config/backup.php run:
- php artisan vendor:publish --provider="Spatie\Backup\BackupServiceProvider"

## Configuring the backup disk

By default, the backup will be saved into the <p style="color:red;">storage/app/Laravel/</p> directory of your laravel application. We recommend that you create a disk named backups (you can use any name you prefer) in filesystems.php and specify that name in the disk key of the backup.php config file.

## Scheduling

After you have performed the basic installation you can start using the <p style="color:red;">backup:run, backup:clean, backup:list and backup:monitor-commands</p>. In most cases you'll want to schedule these commands so you don't have to manually run backup:run everytime you need a new backup.

The commands can be scheduled in Laravel's console kernel, just like any other command.

// app/Console/Kernel.php

protected function schedule(Schedule $schedule)
{
   $schedule->command('backup:clean')->daily()->at('01:00');
   $schedule->command('backup:run')->daily()->at('01:30');
}



*** only database backup command:
-> php artisan backup:run --only-db


reference video:
1. https://www.youtube.com/watch?v=OPDkQ3V4Goo
2. https://www.youtube.com/watch?v=6kxXkrlRuJU&list=PL41H_cEq1COgIJB-5WSGS-rhXajQfws7f&index=5&ab_channel=QiroLab

