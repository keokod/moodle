Pour un clonage rapide, il nous faut récupérer le dossier:

/theme/boost


dupliquer le dossier boost et le renommer , ici je l'ai appelé "keo".

une fois le dossier  keo mis en place, il nous fait avec un logiciel d'édition de code récent comme visual studio ou netbeans ,

il nous faut modifier tous les chaines dans les fichiers contenant "_boost" par "_keo".

recommencer avec "boost_" par "keo_".

Rechercher les noms fichiers des occurences "boost" avec ls et un grep

 ls -R | grep boost
theme_boost.php
behat_theme_boost_behat_action_menu.php
behat_theme_boost_behat_admin.php
behat_theme_boost_behat_blocks.php
behat_theme_boost_behat_course.php
behat_theme_boost_behat_filepicker.php
behat_theme_boost_behat_files.php
behat_theme_boost_behat_grade.php
behat_theme_boost_behat_mod_quiz.php
behat_theme_boost_behat_navigation.php
behat_theme_boost_behat_repository_upload.php


il faudra changer tout les noms des fichiers contenant "boost" par "keo".

Dans settings.php modifier cette ligne:


defined('MOODLE_INTERNAL') || die();

if ($ADMIN->fulltree) {
    $settings = new theme_keo_admin_settingspage_tabs('themesettingboost', get_string('configtitle', 'theme_keo'));
    $page = new admin_settingpage('theme_keo_general', get_string('generalsettings', 'theme_keo'));

par:

    $settings = new theme_keo_admin_settingspage_tabs('themesettingkeo, get_string('configtitle', 'theme_keo'));

Une dernière chose à faire , dans le fichier /lang/en/theme_keo.php

modifier le nom du thème "Boost" par "boost".

puis dans le fichier config.php changer le nom du thème

$THEME->name ='keo'

modifier les occurence des chaines dans les fichier "Boost" par "Keo" (B en majuscule)


Si le nom de boost est déjà existant, lors de la liste des thèmes à choisir, le thème "keo" n'existera pas!

pour vérifier que le scss foncionne remplaçons une valeur de couleur dans le menu déroulant dans le fichier _variables.scss
(ligne 449) $dropdown-bg : red !defaut;
vider le cache avec la commande
/admin/cli$ php purge_caches.php

aller à la page moodle et faître descendre un menu par exemple le langague, normalement vous devrier avoir un fond rouge du sous menu.

