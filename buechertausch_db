-- phpMyAdmin SQL Dump
-- version 5.2.1
-- https://www.phpmyadmin.net/
--
-- Host: 127.0.0.1
-- Erstellungszeit: 27. Okt 2026 um 15:17
-- Server-Version: 10.4.32-MariaDB
-- PHP-Version: 8.2.12

SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
START TRANSACTION;
SET time_zone = "+00:00";


/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8mb4 */;

--
-- Datenbank: `buechertausch_db`
--
CREATE DATABASE IF NOT EXISTS `buechertausch_db` DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;
USE `buechertausch_db`;

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `adresse`
--

CREATE TABLE `adresse` (
  `adresse_id` int(11) NOT NULL,
  `landname` varchar(50) NOT NULL,
  `postleitzahl` varchar(10) NOT NULL,
  `ortsname` varchar(50) NOT NULL,
  `strasse` varchar(50) NOT NULL,
  `hausnummer` varchar(10) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Daten für Tabelle `adresse`
--

INSERT INTO `adresse` (`adresse_id`, `landname`, `postleitzahl`, `ortsname`, `strasse`, `hausnummer`) VALUES
(1, 'Deutschland', '90402', 'Nürnberg', 'Königstraße', '12'),
(2, 'Deutschland', '10115', 'Berlin', 'Invalidenstraße', '44'),
(3, 'Deutschland', '80331', 'München', 'Marienplatz', '8'),
(4, 'Deutschland', '50667', 'Köln', 'Hohe Straße', '71'),
(5, 'Deutschland', '20095', 'Hamburg', 'Mönckebergstraße', '19'),
(6, 'Deutschland', '70173', 'Stuttgart', 'Königstraße', '22'),
(7, 'Deutschland', '1067', 'Dresden', 'Prager Straße', '5'),
(8, 'Deutschland', '28195', 'Bremen', 'Obernstraße', '33'),
(9, 'Deutschland', '90403', 'Nürnberg', 'Weinmarkt', '4'),
(10, 'Deutschland', '4109', 'Leipzig', 'Petersstraße', '15');

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `adressenzuordnung`
--

CREATE TABLE `adressenzuordnung` (
  `adresse_id` int(11) NOT NULL,
  `user_id` int(11) NOT NULL,
  `adresse_bezeichnung` enum('Erstwohnsitz','Zweitwohnsitz','Arbeitsort','Urlaubssitz') NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Daten für Tabelle `adressenzuordnung`
--

INSERT INTO `adressenzuordnung` (`adresse_id`, `user_id`, `adresse_bezeichnung`) VALUES
(1, 1, 'Erstwohnsitz'),
(2, 1, 'Arbeitsort'),
(3, 2, 'Erstwohnsitz'),
(4, 3, 'Erstwohnsitz'),
(5, 3, 'Zweitwohnsitz'),
(6, 4, 'Erstwohnsitz'),
(7, 5, 'Erstwohnsitz'),
(8, 5, 'Urlaubssitz'),
(9, 6, 'Erstwohnsitz'),
(10, 7, 'Erstwohnsitz');

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `ausgabe`
--

CREATE TABLE `ausgabe` (
  `ausgabe_id` int(11) NOT NULL,
  `buch_id` int(11) NOT NULL,
  `ausgabe` varchar(20) NOT NULL,
  `verlag_id` int(11) NOT NULL,
  `format` enum('Hardcover','Taschenbuch') NOT NULL,
  `status` enum('neu','geprüft') NOT NULL DEFAULT 'neu',
  `quelle` enum('User','API') NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Daten für Tabelle `ausgabe`
--

INSERT INTO `ausgabe` (`ausgabe_id`, `buch_id`, `ausgabe`, `verlag_id`, `format`, `status`, `quelle`) VALUES
(1, 1, '1. Auflage', 1, 'Hardcover', 'geprüft', 'User'),
(2, 2, '2. Auflage', 1, 'Taschenbuch', 'geprüft', 'User'),
(3, 3, '1. Auflage', 2, 'Hardcover', 'neu', 'API'),
(4, 4, '1. Auflage', 2, 'Taschenbuch', 'geprüft', 'API'),
(5, 5, '3. Auflage', 3, 'Taschenbuch', 'geprüft', 'User'),
(6, 6, '1. Auflage', 4, 'Hardcover', 'geprüft', 'User'),
(7, 7, '1. Auflage', 5, 'Taschenbuch', 'neu', 'User'),
(8, 8, '2. Auflage', 7, 'Hardcover', 'geprüft', 'API'),
(9, 9, '1. Auflage', 9, 'Hardcover', 'geprüft', 'User'),
(10, 10, '1. Auflage', 10, 'Taschenbuch', 'neu', 'User');

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `ausleihvorgang`
--

CREATE TABLE `ausleihvorgang` (
  `ausleih_id` int(11) NOT NULL,
  `verleiher` int(11) DEFAULT NULL,
  `ausleiher` int(11) DEFAULT NULL,
  `exemplar_id` int(11) DEFAULT NULL,
  `status` enum('In Ausleihe','Rückgabe erfolgt','Abgeschlossen') NOT NULL DEFAULT 'In Ausleihe',
  `datum_ausleihe` date NOT NULL DEFAULT curdate(),
  `frist` date NOT NULL,
  `datum_rueckgabe` date DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Daten für Tabelle `ausleihvorgang`
--

INSERT INTO `ausleihvorgang` (`ausleih_id`, `verleiher`, `ausleiher`, `exemplar_id`, `status`, `datum_ausleihe`, `frist`, `datum_rueckgabe`) VALUES
(1, 1, 2, 1, 'In Ausleihe', '2024-02-01', '2024-02-15', NULL),
(2, 2, 3, 2, 'Rückgabe erfolgt', '2024-01-10', '2024-01-20', '2024-01-18'),
(3, 3, 4, 3, 'Abgeschlossen', '2024-03-05', '2024-03-20', '2024-03-19'),
(4, 4, 5, 4, 'In Ausleihe', '2024-04-01', '2024-04-14', NULL),
(5, 5, 6, 5, 'Rückgabe erfolgt', '2024-02-12', '2024-02-25', '2024-02-23'),
(6, 6, 7, 6, 'Abgeschlossen', '2024-01-15', '2024-01-30', '2024-01-29'),
(7, 7, 8, 7, 'In Ausleihe', '2024-03-20', '2024-04-03', NULL),
(8, 8, 9, 8, 'Rückgabe erfolgt', '2024-02-05', '2024-02-18', '2024-02-17'),
(9, 9, 10, 9, 'Abgeschlossen', '2024-04-10', '2024-04-24', '2024-04-22'),
(10, NULL, 1, 10, 'In Ausleihe', '2024-05-01', '2024-05-15', NULL);

--
-- Trigger `ausleihvorgang`
--
DELIMITER $$
CREATE TRIGGER `trg_ausleihvorgang_set_rueckgabe` BEFORE UPDATE ON `ausleihvorgang` FOR EACH ROW BEGIN
    IF NEW.status = 'Rückgabe erfolgt'
       AND OLD.status <> 'Rückgabe erfolgt'
       AND NEW.datum_rueckgabe IS NULL THEN
        SET NEW.datum_rueckgabe = CURRENT_DATE;
    END IF;
END
$$
DELIMITER ;
DELIMITER $$
CREATE TRIGGER `trg_exemplar_set_unavailable` AFTER INSERT ON `ausleihvorgang` FOR EACH ROW BEGIN
    -- Nur ausführen, wenn ein Exemplar angegeben ist
    IF NEW.exemplar_id IS NOT NULL THEN
        UPDATE Exemplar
        SET verfuegbar = 0
        WHERE exemplar_id = NEW.exemplar_id;
    END IF;
END
$$
DELIMITER ;
DELIMITER $$
CREATE TRIGGER `trg_exemplar_verfuegbar_nach_rueckgabe` AFTER UPDATE ON `ausleihvorgang` FOR EACH ROW BEGIN
    IF NEW.status = 'Abgeschlossen'
       AND OLD.status <> 'Abgeschlossen'
       AND NOT EXISTS (
           SELECT 1
           FROM Nichtverfuegbarkeitszeitraum n
           WHERE n.exemplar_id = NEW.exemplar_id
             AND NEW.datum_rueckgabe BETWEEN n.startdatum AND n.enddatum
       )
    THEN
        UPDATE Exemplar
        SET verfuegbar = 1
        WHERE exemplar_id = NEW.exemplar_id;
    END IF;
END
$$
DELIMITER ;
DELIMITER $$
CREATE TRIGGER `trg_lesehistorie_nach_abschluss` AFTER UPDATE ON `ausleihvorgang` FOR EACH ROW BEGIN
    IF NEW.status = 'Rückgabe erfolgt'
       AND OLD.status <> 'Rückgabe erfolgt'
       AND NEW.ausleiher IS NOT NULL
    THEN
        INSERT INTO Lesehistorie (user_id, exemplar_id)
        VALUES (NEW.ausleiher, NEW.exemplar_id);
    END IF;
END
$$
DELIMITER ;

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `ausleihvorgang_archiv`
--

CREATE TABLE `ausleihvorgang_archiv` (
  `ausleih_id` int(11) NOT NULL,
  `verleiher` int(11) DEFAULT NULL,
  `ausleiher` int(11) DEFAULT NULL,
  `exemplar_id` int(11) DEFAULT NULL,
  `status` enum('In Ausleihe','Rückgabe erfolgt','Abgeschlossen') NOT NULL DEFAULT 'In Ausleihe',
  `datum_ausleihe` date NOT NULL DEFAULT curdate(),
  `frist` date NOT NULL,
  `datum_rueckgabe` date DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Daten für Tabelle `ausleihvorgang_archiv`
--

INSERT INTO `ausleihvorgang_archiv` (`ausleih_id`, `verleiher`, `ausleiher`, `exemplar_id`, `status`, `datum_ausleihe`, `frist`, `datum_rueckgabe`) VALUES
(1, 1, 2, 1, 'In Ausleihe', '2024-02-01', '2024-02-15', NULL),
(2, 2, 3, 2, 'Rückgabe erfolgt', '2024-01-10', '2024-01-20', '2024-01-18'),
(3, 3, 4, 3, 'Abgeschlossen', '2024-03-05', '2024-03-20', '2024-03-19'),
(4, 4, 5, 4, 'In Ausleihe', '2024-04-01', '2024-04-14', NULL),
(5, 5, 6, 5, 'Rückgabe erfolgt', '2024-02-12', '2024-02-25', '2024-02-23'),
(6, 6, 7, 6, 'Abgeschlossen', '2024-01-15', '2024-01-30', '2024-01-29'),
(7, 7, 8, 7, 'In Ausleihe', '2024-03-20', '2024-04-03', NULL),
(8, 8, 9, 8, 'Rückgabe erfolgt', '2024-02-05', '2024-02-18', '2024-02-17'),
(9, 9, 10, 9, 'Abgeschlossen', '2024-04-10', '2024-04-24', '2024-04-22'),
(10, NULL, 1, 10, 'In Ausleihe', '2024-05-01', '2024-05-15', NULL);

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `autor`
--

CREATE TABLE `autor` (
  `autor_id` int(11) NOT NULL,
  `vorname` varchar(25) NOT NULL,
  `nachname` varchar(25) NOT NULL,
  `geburtstag` int(11) DEFAULT NULL,
  `geburtsmonat` int(11) DEFAULT NULL,
  `geburtsjahr` int(11) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Daten für Tabelle `autor`
--

INSERT INTO `autor` (`autor_id`, `vorname`, `nachname`, `geburtstag`, `geburtsmonat`, `geburtsjahr`) VALUES
(1, 'Anna', 'Weigand', 12, 5, 1984),
(2, 'Markus', 'Feldmann', NULL, NULL, 1978),
(3, 'Clara', 'Hoffstetter', 3, 11, 1990),
(4, 'Jonas', 'Berendt', 21, 2, 1982),
(5, 'Sophie', 'Altenburg', NULL, 7, 1975),
(6, 'Leon', 'Gruber', 9, 9, 1988),
(7, 'Mara', 'Kleinert', NULL, NULL, NULL),
(8, 'Tim', 'Scholz', 14, 1, 1993),
(9, 'Helena', 'Winter', 30, 6, 1980),
(10, 'Paul', 'Neubauer', NULL, 3, 1969);

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `autorenzuordnung`
--

CREATE TABLE `autorenzuordnung` (
  `autor_id` int(11) NOT NULL,
  `buch_id` int(11) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Daten für Tabelle `autorenzuordnung`
--

INSERT INTO `autorenzuordnung` (`autor_id`, `buch_id`) VALUES
(1, 1),
(1, 2),
(2, 3),
(2, 4),
(3, 5),
(4, 6),
(5, 7),
(6, 8),
(7, 9),
(8, 10);

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `bewertung`
--

CREATE TABLE `bewertung` (
  `bewertung_id` int(11) NOT NULL,
  `user_id` int(11) DEFAULT NULL,
  `buch_id` int(11) NOT NULL,
  `sterne` int(11) NOT NULL,
  `bewertungstext` text DEFAULT NULL,
  `zeitstempel` timestamp NOT NULL DEFAULT current_timestamp()
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Daten für Tabelle `bewertung`
--

INSERT INTO `bewertung` (`bewertung_id`, `user_id`, `buch_id`, `sterne`, `bewertungstext`, `zeitstempel`) VALUES
(1, 1, 1, 5, 'Wunderschöne Fantasywelt und toller Schreibstil.', '2024-01-12 13:22:00'),
(2, 2, 3, 4, NULL, '2024-02-03 09:15:00'),
(3, 3, 5, 5, 'Sehr atmosphärischer Krimi, absolut empfehlenswert.', '2024-02-18 17:40:00'),
(4, 4, 4, 3, 'Gute Ideen, aber etwas langatmig in der Mitte.', '2024-03-01 08:05:00'),
(5, 5, 7, 4, 'Schöne Geschichte, perfekt für den Sommer.', '2024-03-12 15:30:00'),
(6, 6, 9, 5, 'Extrem spannend, konnte es kaum weglegen.', '2024-03-25 20:10:00'),
(7, 7, 10, 4, NULL, '2024-04-02 06:50:00'),
(8, 8, 6, 3, 'Interessanter Thriller, aber das Ende war vorhersehbar.', '2024-04-15 17:20:00'),
(9, 9, 2, 5, 'Starke Fortsetzung, noch besser als der erste Teil.', '2024-04-28 09:45:00'),
(10, 10, 8, 4, 'Gut recherchiert und sehr informativ.', '2024-05-05 11:55:00');

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `buch`
--

CREATE TABLE `buch` (
  `buch_id` int(11) NOT NULL,
  `reihe_id` int(11) NOT NULL,
  `band` int(11) DEFAULT NULL,
  `titel` varchar(100) NOT NULL,
  `jahr_erstveroeffentlichung` int(11) NOT NULL,
  `originalsprache` varchar(20) NOT NULL,
  `status` enum('neu','geprüft') NOT NULL DEFAULT 'neu',
  `quelle` enum('User','API') NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Daten für Tabelle `buch`
--

INSERT INTO `buch` (`buch_id`, `reihe_id`, `band`, `titel`, `jahr_erstveroeffentlichung`, `originalsprache`, `status`, `quelle`) VALUES
(1, 1, 1, 'Der Ruf der Alten Magie', 2012, 'Deutsch', 'geprüft', 'User'),
(2, 1, 2, 'Die Schatten von Avaron', 2014, 'Deutsch', 'geprüft', 'User'),
(3, 2, 1, 'Sternenbund – Aufbruch ins Unbekannte', 2018, 'Englisch', 'neu', 'API'),
(4, 2, 2, 'Sternenbund – Der letzte Außenposten', 2020, 'Englisch', 'geprüft', 'API'),
(5, 3, 1, 'Kommissar Bremer und der stille See', 2010, 'Deutsch', 'geprüft', 'User'),
(6, 4, 1, 'Berlin Dunkel – Der erste Fall', 2016, 'Deutsch', 'geprüft', 'User'),
(7, 5, 1, 'Sommer am See – Neubeginn', 2019, 'Deutsch', 'neu', 'User'),
(8, 6, 1, 'Zeitenwende – Der Fall der Mauer', 2008, 'Deutsch', 'geprüft', 'API'),
(9, 9, 1, 'Nachtjäger – Blutmond', 2015, 'Englisch', 'geprüft', 'User'),
(10, 10, 1, 'Die kleinen Füchse im Wald', 2021, 'Deutsch', 'neu', 'User');

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `exemplar`
--

CREATE TABLE `exemplar` (
  `exemplar_id` int(11) NOT NULL,
  `ausgabe_id` int(11) NOT NULL,
  `user_id_besitzer` int(11) NOT NULL,
  `adresse_id` int(11) NOT NULL,
  `versand` tinyint(1) NOT NULL DEFAULT 0,
  `versandpreis` decimal(4,2) DEFAULT NULL,
  `verfuegbar` tinyint(1) NOT NULL DEFAULT 1
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Daten für Tabelle `exemplar`
--

INSERT INTO `exemplar` (`exemplar_id`, `ausgabe_id`, `user_id_besitzer`, `adresse_id`, `versand`, `versandpreis`, `verfuegbar`) VALUES
(1, 1, 1, 1, 0, NULL, 0),
(2, 2, 2, 2, 1, 3.90, 0),
(3, 3, 3, 3, 1, 4.50, 0),
(4, 4, 4, 4, 0, NULL, 0),
(5, 5, 5, 5, 1, 2.90, 0),
(6, 6, 6, 6, 0, NULL, 0),
(7, 7, 7, 7, 1, 3.50, 0),
(8, 8, 8, 8, 1, 4.90, 0),
(9, 9, 9, 9, 0, NULL, 0),
(10, 10, 10, 10, 1, 2.50, 0);

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `externe_transaktion`
--

CREATE TABLE `externe_transaktion` (
  `schadensmeldung_id` int(11) NOT NULL,
  `transaktions_id` varchar(100) NOT NULL,
  `dienstleister` enum('PayPal','Klarna') NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Daten für Tabelle `externe_transaktion`
--

INSERT INTO `externe_transaktion` (`schadensmeldung_id`, `transaktions_id`, `dienstleister`) VALUES
(1, 'PP-20240210-AB12CD34', 'PayPal'),
(2, 'KL-20240120-ZX98YU76', 'Klarna'),
(2, 'PP-20240121-FF22GG33', 'PayPal'),
(3, 'PP-20240306-QQ11RR22', 'PayPal'),
(4, 'PP-20240225-CC11DD22', 'PayPal'),
(5, 'KL-20240312-SS33TT44', 'Klarna'),
(6, 'KL-20240202-AA77BB88', 'Klarna'),
(7, 'PP-20240320-UU55VV66', 'PayPal'),
(8, 'PP-20240207-HH44JJ55', 'PayPal'),
(10, 'KL-20240501-MM66NN77', 'Klarna');

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `genre`
--

CREATE TABLE `genre` (
  `genre_id` int(11) NOT NULL,
  `genre_name` varchar(20) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Daten für Tabelle `genre`
--

INSERT INTO `genre` (`genre_id`, `genre_name`) VALUES
(8, 'Biografie'),
(1, 'Fantasy'),
(6, 'Historischer Roman'),
(9, 'Horror'),
(10, 'Kinderbuch'),
(3, 'Krimi'),
(5, 'Romance'),
(7, 'Sachbuch'),
(2, 'Science Fiction'),
(4, 'Thriller');

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `genrezuordnung`
--

CREATE TABLE `genrezuordnung` (
  `genre_id` int(11) NOT NULL,
  `buch_id` int(11) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Daten für Tabelle `genrezuordnung`
--

INSERT INTO `genrezuordnung` (`genre_id`, `buch_id`) VALUES
(1, 1),
(1, 2),
(2, 3),
(2, 4),
(3, 5),
(4, 6),
(5, 7),
(6, 8),
(9, 9),
(10, 10);

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `lesehistorie`
--

CREATE TABLE `lesehistorie` (
  `user_id` int(11) NOT NULL,
  `exemplar_id` int(11) NOT NULL,
  `zeitstempel` timestamp NOT NULL DEFAULT current_timestamp()
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Daten für Tabelle `lesehistorie`
--

INSERT INTO `lesehistorie` (`user_id`, `exemplar_id`, `zeitstempel`) VALUES
(1, 1, '2024-01-12 14:10:00'),
(5, 7, '2024-01-28 13:00:00'),
(1, 3, '2024-02-05 17:45:00'),
(5, 8, '2024-02-10 09:25:00'),
(3, 4, '2024-02-20 19:15:00'),
(2, 5, '2024-03-01 08:30:00'),
(7, 10, '2024-03-03 10:50:00'),
(2, 2, '2026-05-11 17:06:20'),
(4, 6, '2026-05-11 17:06:20'),
(6, 9, '2026-05-11 17:06:20');

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `lesehistorie_archiv`
--

CREATE TABLE `lesehistorie_archiv` (
  `user_id` int(11) NOT NULL,
  `exemplar_id` int(11) NOT NULL,
  `zeitstempel` timestamp NOT NULL DEFAULT current_timestamp()
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `meldungsbeweis`
--

CREATE TABLE `meldungsbeweis` (
  `meldungsbeweis_id` int(11) NOT NULL,
  `usermeldung_id` int(11) NOT NULL,
  `bilddatei` mediumblob NOT NULL,
  `eingereicht_von` int(11) DEFAULT NULL,
  `beweisart` enum('Usermeldung','Gegenbeweis') NOT NULL,
  `zeitpunkt_aufnahme` timestamp NULL DEFAULT NULL,
  `zeitpunkt_des_einreichens` timestamp NOT NULL DEFAULT current_timestamp()
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Daten für Tabelle `meldungsbeweis`
--

INSERT INTO `meldungsbeweis` (`meldungsbeweis_id`, `usermeldung_id`, `bilddatei`, `eingereicht_von`, `beweisart`, `zeitpunkt_aufnahme`, `zeitpunkt_des_einreichens`) VALUES
(1, 1, 0xffd8ffe0, 1, 'Usermeldung', '2024-02-01 11:15:00', '2024-02-01 11:20:00'),
(2, 2, 0xffd8ffe0, 3, 'Usermeldung', '2024-03-05 08:40:00', '2024-03-05 08:45:00'),
(3, 2, 0xffd8ffe0, 4, 'Gegenbeweis', NULL, '2024-03-06 09:15:00'),
(4, 3, 0xffd8ffe0, 5, 'Usermeldung', '2024-01-20 13:20:00', '2024-01-20 13:25:00'),
(5, 4, 0xffd8ffe0, 7, 'Usermeldung', '2024-03-12 10:45:00', '2024-03-12 10:50:00'),
(6, 4, 0xffd8ffe0, 8, 'Gegenbeweis', '2024-03-13 08:10:00', '2024-03-13 08:12:00'),
(7, 6, 0xffd8ffe0, 4, 'Usermeldung', NULL, '2024-02-22 12:10:00'),
(8, 7, 0xffd8ffe0, 6, 'Usermeldung', '2024-01-28 17:05:00', '2024-01-28 17:10:00'),
(9, 9, 0xffd8ffe0, 9, 'Usermeldung', '2024-04-01 14:20:00', '2024-04-01 14:25:00'),
(10, 10, 0xffd8ffe0, NULL, 'Usermeldung', NULL, '2024-05-01 08:25:00');

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `meldungsbeweis_archiv`
--

CREATE TABLE `meldungsbeweis_archiv` (
  `meldungsbeweis_id` int(11) NOT NULL,
  `usermeldung_id` int(11) NOT NULL,
  `bilddatei` mediumblob NOT NULL,
  `eingereicht_von` int(11) DEFAULT NULL,
  `beweisart` enum('Usermeldung','Gegenbeweis') NOT NULL,
  `zeitpunkt_aufnahme` timestamp NULL DEFAULT NULL,
  `zeitpunkt_des_einreichens` timestamp NOT NULL DEFAULT current_timestamp()
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `meldungsgrund`
--

CREATE TABLE `meldungsgrund` (
  `meldungsgrund_id` int(11) NOT NULL,
  `meldungsgrund` varchar(50) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Daten für Tabelle `meldungsgrund`
--

INSERT INTO `meldungsgrund` (`meldungsgrund_id`, `meldungsgrund`) VALUES
(1, 'Unhöfliches Verhalten'),
(2, 'Verspätete Rückgabe'),
(3, 'Beschädigtes Exemplar'),
(4, 'Spam-Nachrichten'),
(5, 'Falsche Angaben'),
(6, 'Unvollständige Rückgabe'),
(7, 'Belästigendes Verhalten'),
(8, 'Unzuverlässige Kommunikation'),
(9, 'Regelverstoß'),
(10, 'Ungewöhnliche Aktivität');

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `meldungsgrundzuordnung`
--

CREATE TABLE `meldungsgrundzuordnung` (
  `usermeldung_id` int(11) NOT NULL,
  `meldungsgrund_id` int(11) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Daten für Tabelle `meldungsgrundzuordnung`
--

INSERT INTO `meldungsgrundzuordnung` (`usermeldung_id`, `meldungsgrund_id`) VALUES
(1, 1),
(2, 2),
(3, 3),
(4, 4),
(5, 1),
(6, 6),
(7, 2),
(7, 8),
(8, 1),
(9, 5),
(10, 10);

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `merkliste_buch`
--

CREATE TABLE `merkliste_buch` (
  `user_id` int(11) NOT NULL,
  `buch_id` int(11) NOT NULL,
  `zeitstempel` timestamp NOT NULL DEFAULT current_timestamp()
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Daten für Tabelle `merkliste_buch`
--

INSERT INTO `merkliste_buch` (`user_id`, `buch_id`, `zeitstempel`) VALUES
(1, 3, '2024-02-10 13:20:00'),
(1, 7, '2024-02-11 08:15:00'),
(2, 1, '2024-01-25 17:40:00'),
(2, 5, '2024-02-02 09:05:00'),
(3, 2, '2024-03-01 11:30:00'),
(4, 4, '2024-03-12 07:55:00'),
(4, 9, '2024-03-12 08:10:00'),
(5, 10, '2024-01-18 15:45:00'),
(6, 6, '2024-04-05 18:10:00'),
(7, 8, '2024-02-28 10:22:00');

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `merkliste_exemplar`
--

CREATE TABLE `merkliste_exemplar` (
  `user_id` int(11) NOT NULL,
  `exemplar_id` int(11) NOT NULL,
  `zeitstempel` timestamp NOT NULL DEFAULT current_timestamp()
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Daten für Tabelle `merkliste_exemplar`
--

INSERT INTO `merkliste_exemplar` (`user_id`, `exemplar_id`, `zeitstempel`) VALUES
(1, 2, '2024-02-10 13:30:00'),
(1, 5, '2024-02-11 08:45:00'),
(2, 1, '2024-01-26 16:10:00'),
(2, 3, '2026-05-11 17:04:24'),
(3, 4, '2024-03-02 11:05:00'),
(4, 6, '2026-05-11 17:04:24'),
(4, 7, '2024-03-15 07:20:00'),
(5, 9, '2024-01-19 15:00:00'),
(6, 8, '2026-05-11 17:04:24'),
(7, 10, '2024-02-28 10:40:00');

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `nachricht`
--

CREATE TABLE `nachricht` (
  `sender` int(11) NOT NULL,
  `empfaenger` int(11) NOT NULL,
  `inhalt` text NOT NULL,
  `zeitpunkt_des_sendens` timestamp NOT NULL DEFAULT current_timestamp()
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Daten für Tabelle `nachricht`
--

INSERT INTO `nachricht` (`sender`, `empfaenger`, `inhalt`, `zeitpunkt_des_sendens`) VALUES
(1, 2, 'Hey, wäre es möglich, das Exemplar nächste Woche auszuleihen?', '2024-02-01 13:20:00'),
(2, 1, 'Klar, sag einfach Bescheid, wann du Zeit hast.', '2024-02-01 13:32:00'),
(3, 4, 'Hi, ich habe dein Buch fast durch. Soll ich es dir am Wochenende zurückbringen?', '2024-03-05 17:10:00'),
(4, 3, 'Ja, das passt super. Danke dir!', '2024-03-05 17:22:00'),
(5, 6, 'Hallo, ist dein Thriller noch verfügbar?', '2026-05-11 17:07:32'),
(6, 5, 'Ja, kannst du gerne ausleihen. Ich bin morgen zuhause.', '2024-01-20 08:15:00'),
(7, 8, 'Hi, ich habe gesehen, dass du das Buch auch magst. Wollen wir tauschen?', '2024-03-12 10:40:00'),
(8, 7, 'Gerne! Ich schicke dir später meine Adresse.', '2024-03-12 10:55:00'),
(9, 10, 'Hey, danke für die schnelle Rückgabe!', '2024-04-02 14:05:00'),
(10, 9, 'Kein Problem, hat Spaß gemacht zu lesen.', '2026-05-11 17:07:32');

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `nachricht_archiv`
--

CREATE TABLE `nachricht_archiv` (
  `sender` int(11) NOT NULL,
  `empfaenger` int(11) NOT NULL,
  `inhalt` text NOT NULL,
  `zeitpunkt_des_sendens` timestamp NOT NULL DEFAULT current_timestamp()
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `nichtverfuegbarkeitszeitraum`
--

CREATE TABLE `nichtverfuegbarkeitszeitraum` (
  `exemplar_id` int(11) NOT NULL,
  `startdatum` date NOT NULL,
  `enddatum` date NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Daten für Tabelle `nichtverfuegbarkeitszeitraum`
--

INSERT INTO `nichtverfuegbarkeitszeitraum` (`exemplar_id`, `startdatum`, `enddatum`) VALUES
(1, '2024-02-10', '2024-02-15'),
(2, '2024-03-01', '2024-03-05'),
(3, '2024-01-20', '2024-01-22'),
(4, '2024-04-10', '2024-04-18'),
(5, '2024-02-01', '2024-02-03'),
(6, '2024-05-05', '2024-05-12'),
(7, '2024-03-15', '2024-03-20'),
(8, '2024-01-05', '2024-01-10'),
(9, '2024-04-01', '2024-04-02'),
(10, '2024-02-20', '2024-02-28');

--
-- Trigger `nichtverfuegbarkeitszeitraum`
--
DELIMITER $$
CREATE TRIGGER `trg_exemplar_nichtverfuegbar_start` AFTER INSERT ON `nichtverfuegbarkeitszeitraum` FOR EACH ROW BEGIN
    UPDATE Exemplar
    SET verfuegbar = 0
    WHERE exemplar_id = NEW.exemplar_id
    	AND CURDATE() BETWEEN NEW.startdatum AND NEW.enddatum;
END
$$
DELIMITER ;

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `praeferenz`
--

CREATE TABLE `praeferenz` (
  `user_id` int(11) NOT NULL,
  `genre_id` int(11) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Daten für Tabelle `praeferenz`
--

INSERT INTO `praeferenz` (`user_id`, `genre_id`) VALUES
(1, 1),
(1, 5),
(2, 3),
(2, 4),
(3, 1),
(3, 2),
(4, 3),
(4, 7),
(5, 5),
(5, 6),
(6, 2),
(6, 9),
(7, 5),
(7, 10),
(8, 7),
(8, 8),
(9, 1),
(9, 6),
(10, 3),
(10, 4);

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `reihe`
--

CREATE TABLE `reihe` (
  `reihe_id` int(11) NOT NULL,
  `reihentitel` varchar(100) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Daten für Tabelle `reihe`
--

INSERT INTO `reihe` (`reihe_id`, `reihentitel`) VALUES
(1, 'Die Chroniken von Avaron'),
(2, 'Sternenbund-Saga'),
(3, 'Kommissar Bremer Fälle'),
(4, 'Psychothriller-Reihe Berlin'),
(5, 'Herzklopfen am See'),
(6, 'Zeitenwende-Trilogie'),
(7, 'Wissen Kompakt'),
(8, 'Leben großer Persönlichkeiten'),
(9, 'Nachtjäger-Horrorserie'),
(10, 'Abenteuer der kleinen Füchse');

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `schadensbeweis`
--

CREATE TABLE `schadensbeweis` (
  `schadensbeweis_id` int(11) NOT NULL,
  `schadensmeldung_id` int(11) NOT NULL,
  `bilddatei` mediumblob NOT NULL,
  `eingereicht_von` int(11) DEFAULT NULL,
  `beweisart` enum('Schadensmeldung','Gegenbeweis') NOT NULL,
  `zeitpunkt_aufnahme` timestamp NULL DEFAULT NULL,
  `zeitpunkt_des_einreichens` timestamp NOT NULL DEFAULT current_timestamp()
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Daten für Tabelle `schadensbeweis`
--

INSERT INTO `schadensbeweis` (`schadensbeweis_id`, `schadensmeldung_id`, `bilddatei`, `eingereicht_von`, `beweisart`, `zeitpunkt_aufnahme`, `zeitpunkt_des_einreichens`) VALUES
(1, 1, 0xffd8ffe0, 2, 'Schadensmeldung', '2024-02-10 13:25:00', '2024-02-10 13:30:00'),
(2, 2, 0xffd8ffe0, 3, 'Schadensmeldung', '2024-01-15 08:40:00', '2024-01-15 08:45:00'),
(3, 2, 0xffd8ffe0, 2, 'Gegenbeweis', '2024-01-18 14:10:00', '2024-01-18 14:12:00'),
(4, 3, 0xffd8ffe0, 4, 'Schadensmeldung', NULL, '2024-03-05 17:20:00'),
(5, 4, 0xffd8ffe0, 5, 'Schadensmeldung', '2024-02-22 10:05:00', '2024-02-22 10:10:00'),
(6, 4, 0xffd8ffe0, NULL, 'Gegenbeweis', NULL, '2024-02-23 07:00:00'),
(7, 5, 0xffd8ffe0, 6, 'Schadensmeldung', '2024-03-12 08:00:00', '2024-03-12 08:05:00'),
(8, 6, 0xffd8ffe0, 7, 'Schadensmeldung', '2024-01-28 16:45:00', '2024-01-28 16:50:00'),
(9, 7, 0xffd8ffe0, 8, 'Schadensmeldung', NULL, '2024-03-20 11:35:00'),
(10, 8, 0xffd8ffe0, 9, 'Schadensmeldung', '2024-02-05 13:15:00', '2024-02-05 13:20:00');

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `schadensbeweis_archiv`
--

CREATE TABLE `schadensbeweis_archiv` (
  `schadensbeweis_id` int(11) NOT NULL,
  `schadensmeldung_id` int(11) NOT NULL,
  `bilddatei` mediumblob NOT NULL,
  `eingereicht_von` int(11) DEFAULT NULL,
  `beweisart` enum('Schadensmeldung','Gegenbeweis') NOT NULL,
  `zeitpunkt_aufnahme` timestamp NULL DEFAULT NULL,
  `zeitpunkt_des_einreichens` timestamp NOT NULL DEFAULT current_timestamp()
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `schadensmeldung`
--

CREATE TABLE `schadensmeldung` (
  `schadensmeldung_id` int(11) NOT NULL,
  `verleiher` int(11) DEFAULT NULL,
  `ausleiher` int(11) DEFAULT NULL,
  `exemplar_id` int(11) DEFAULT NULL,
  `schadensbeschreibung` text NOT NULL,
  `status` enum('Aktiv','Beendet') NOT NULL DEFAULT 'Aktiv',
  `zeitpunkt_meldung` timestamp NOT NULL DEFAULT current_timestamp(),
  `zeitpunkt_abschluss` timestamp NULL DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Daten für Tabelle `schadensmeldung`
--

INSERT INTO `schadensmeldung` (`schadensmeldung_id`, `verleiher`, `ausleiher`, `exemplar_id`, `schadensbeschreibung`, `status`, `zeitpunkt_meldung`, `zeitpunkt_abschluss`) VALUES
(1, 1, 2, 1, 'Einband ist eingerissen, vermutlich beim Transport.', 'Aktiv', '2024-02-10 13:20:00', NULL),
(2, 2, 3, 2, 'Mehrere Seiten haben Wasserschäden.', 'Beendet', '2024-01-15 08:30:00', '2024-01-20 15:45:00'),
(3, 3, 4, 3, 'Starke Eselsohren auf den letzten Kapiteln.', 'Aktiv', '2024-03-05 17:10:00', NULL),
(4, 4, 5, 4, 'Kaffeefleck auf Seite 42.', 'Beendet', '2024-02-22 10:00:00', '2024-02-25 12:15:00'),
(5, 5, 6, 5, 'Rückseite des Covers ist abgeknickt.', 'Aktiv', '2024-03-12 07:55:00', NULL),
(6, 6, 7, 6, 'Lose Bindung, Seiten lösen sich.', 'Beendet', '2024-01-28 16:40:00', '2024-02-02 09:00:00'),
(7, 7, 8, 7, 'Leichte Kratzer auf dem Cover.', 'Aktiv', '2024-03-20 11:30:00', NULL),
(8, 8, 9, 8, 'Starker Geruch nach Rauch.', 'Beendet', '2024-02-05 13:10:00', '2024-02-07 08:50:00'),
(9, 9, 10, 9, 'Seiten sind teilweise herausgerissen.', 'Aktiv', '2024-04-01 14:05:00', NULL),
(10, NULL, 1, 10, 'Schmutzflecken auf mehreren Seiten.', 'Aktiv', '2024-05-01 08:15:00', NULL);

--
-- Trigger `schadensmeldung`
--
DELIMITER $$
CREATE TRIGGER `trg_schadensmeldung_set_abschluss` BEFORE UPDATE ON `schadensmeldung` FOR EACH ROW BEGIN
    IF NEW.status = 'Beendet'
       AND OLD.status <> 'Beendet'
       AND NEW.zeitpunkt_abschluss IS NULL THEN
        SET NEW.zeitpunkt_abschluss = CURRENT_TIMESTAMP;
    END IF;
END
$$
DELIMITER ;

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `schadensmeldung_archiv`
--

CREATE TABLE `schadensmeldung_archiv` (
  `schadensmeldung_id` int(11) NOT NULL,
  `verleiher` int(11) DEFAULT NULL,
  `ausleiher` int(11) DEFAULT NULL,
  `exemplar_id` int(11) DEFAULT NULL,
  `schadensbeschreibung` text NOT NULL,
  `status` enum('Aktiv','Beendet') NOT NULL DEFAULT 'Aktiv',
  `zeitpunkt_meldung` timestamp NOT NULL DEFAULT current_timestamp(),
  `zeitpunkt_abschluss` timestamp NULL DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `user`
--

CREATE TABLE `user` (
  `user_id` int(11) NOT NULL,
  `passwort_hash` varchar(64) NOT NULL,
  `vorname` varchar(25) NOT NULL,
  `nachname` varchar(25) NOT NULL,
  `email` varchar(50) NOT NULL,
  `telefonnummer` varchar(20) DEFAULT NULL,
  `status` enum('aktiv','inaktiv','blockiert') NOT NULL DEFAULT 'aktiv'
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Daten für Tabelle `user`
--

INSERT INTO `user` (`user_id`, `passwort_hash`, `vorname`, `nachname`, `email`, `telefonnummer`, `status`) VALUES
(1, 'a94f5374fce5edbc1f1f2b36a3e5e3c1', 'Lena', 'Müller', 'lena.mueller@example.com', '+49 151 23456781', 'aktiv'),
(2, 'b12c9d84e3a1f9c2d4e5f6a7b8c9d0e1', 'Jonas', 'Schmidt', 'jonas.schmidt@example.com', '+49 152 98765432', 'aktiv'),
(3, 'c45d8e12f9a3b7c6d5e4f3a2b1c0d9e8', 'Mara', 'Schneider', 'mara.schneider@example.com', '+49 176 11223344', 'aktiv'),
(4, 'd78e1f23a4b5c6d7e8f9a0b1c2d3e4f5', 'Tim', 'Wagner', 'tim.wagner@example.com', '+49 160 55667788', 'aktiv'),
(5, 'e89f2a34b5c6d7e8f9a0b1c2d3e4f5a6', 'Sophie', 'Becker', 'sophie.becker@example.com', '+49 157 99887766', 'aktiv'),
(6, 'f90a3b45c6d7e8f9a0b1c2d3e4f5a6b7', 'Lukas', 'Hoffmann', 'lukas.hoffmann@example.com', '+49 162 44332211', 'aktiv'),
(7, 'a01b4c56d7e8f9a0b1c2d3e4f5a6b7c8', 'Nina', 'Klein', 'nina.klein@example.com', '+49 171 66778899', 'aktiv'),
(8, 'b12c5d67e8f9a0b1c2d3e4f5a6b7c8d9', 'Paul', 'Schäfer', 'paul.schaefer@example.com', '+49 173 22113344', 'aktiv'),
(9, 'c23d6e78f9a0b1c2d3e4f5a6b7c8d9e0', 'Hannah', 'Koch', 'hannah.koch@example.com', '+49 175 33445566', 'aktiv'),
(10, 'd34e7f89a0b1c2d3e4f5a6b7c8d9e0f1', 'Felix', 'Richter', 'felix.richter@example.com', '+49 178 44556677', 'aktiv');

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `usermeldung`
--

CREATE TABLE `usermeldung` (
  `usermeldung_id` int(11) NOT NULL,
  `melder` int(11) DEFAULT NULL,
  `gemeldeter` int(11) DEFAULT NULL,
  `beschreibung` text DEFAULT NULL,
  `status` enum('Offen','In Prüfung','Abgelehnt','Akzeptiert') NOT NULL DEFAULT 'Offen',
  `zeitpunkt_meldung` timestamp NOT NULL DEFAULT current_timestamp(),
  `zeitpunkt_pruefungsbeginn` timestamp NULL DEFAULT NULL,
  `zeitpunkt_abschluss` timestamp NULL DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Daten für Tabelle `usermeldung`
--

INSERT INTO `usermeldung` (`usermeldung_id`, `melder`, `gemeldeter`, `beschreibung`, `status`, `zeitpunkt_meldung`, `zeitpunkt_pruefungsbeginn`, `zeitpunkt_abschluss`) VALUES
(1, 1, 2, NULL, 'Offen', '2024-02-01 11:10:00', NULL, NULL),
(2, 3, 4, 'Verspätete Rückgabe.', 'In Prüfung', '2024-03-05 08:30:00', '2024-03-06 09:00:00', NULL),
(3, 5, 6, 'Beschädigtes Exemplar zurückgegeben.', 'Akzeptiert', '2024-01-20 13:15:00', '2024-01-21 07:00:00', '2024-01-25 15:30:00'),
(4, 7, 8, 'Spam-Nachrichten.', 'Abgelehnt', '2024-03-12 10:40:00', '2024-03-13 08:00:00', '2024-03-14 14:20:00'),
(5, 2, 1, NULL, 'Offen', '2024-02-10 16:50:00', NULL, NULL),
(6, 4, 3, 'Unvollständige Rückgabe.', 'In Prüfung', '2024-02-22 12:05:00', '2024-02-23 09:30:00', NULL),
(7, 6, 5, NULL, 'Akzeptiert', '2024-01-28 17:00:00', '2024-01-29 08:15:00', '2024-02-01 13:45:00'),
(8, 8, 7, 'Unfreundlicher Umgangston.', 'Offen', '2024-03-20 11:50:00', NULL, NULL),
(9, 9, 10, 'Falsche Angaben zur Verfügbarkeit.', 'In Prüfung', '2024-04-01 14:10:00', '2024-04-02 06:30:00', NULL),
(10, NULL, 9, 'Automatische Systemmeldung wegen ungewöhnlicher Aktivität.', 'Offen', '2024-05-01 08:20:00', NULL, NULL);

--
-- Trigger `usermeldung`
--
DELIMITER $$
CREATE TRIGGER `trg_usermeldung_set_abschluss` BEFORE UPDATE ON `usermeldung` FOR EACH ROW BEGIN
    IF (NEW.status IN ('Abgelehnt', 'Akzeptiert'))
       AND (OLD.status NOT IN ('Abgelehnt', 'Akzeptiert'))
       AND NEW.zeitpunkt_abschluss IS NULL THEN
        SET NEW.zeitpunkt_abschluss = CURRENT_TIMESTAMP;
    END IF;
END
$$
DELIMITER ;
DELIMITER $$
CREATE TRIGGER `trg_usermeldung_set_pruefung` BEFORE UPDATE ON `usermeldung` FOR EACH ROW BEGIN
    IF NEW.status = 'In Prüfung'
       AND OLD.status <> 'In Prüfung'
       AND NEW.zeitpunkt_pruefungsbeginn IS NULL THEN
        SET NEW.zeitpunkt_pruefungsbeginn = CURRENT_TIMESTAMP;
    END IF;
END
$$
DELIMITER ;

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `usermeldung_archiv`
--

CREATE TABLE `usermeldung_archiv` (
  `usermeldung_id` int(11) NOT NULL,
  `melder` int(11) DEFAULT NULL,
  `gemeldeter` int(11) DEFAULT NULL,
  `beschreibung` text DEFAULT NULL,
  `status` enum('Offen','In Prüfung','Abgelehnt','Akzeptiert') NOT NULL DEFAULT 'Offen',
  `zeitpunkt_meldung` timestamp NOT NULL DEFAULT current_timestamp(),
  `zeitpunkt_pruefungsbeginn` timestamp NULL DEFAULT NULL,
  `zeitpunkt_abschluss` timestamp NULL DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- --------------------------------------------------------

--
-- Tabellenstruktur für Tabelle `verlag`
--

CREATE TABLE `verlag` (
  `verlag_id` int(11) NOT NULL,
  `name` varchar(25) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Daten für Tabelle `verlag`
--

INSERT INTO `verlag` (`verlag_id`, `name`) VALUES
(5, 'Berg & Tal Verlag'),
(6, 'Edition Morgenstern'),
(1, 'Falkenstein Verlag'),
(4, 'Hanseatische Literaturwer'),
(8, 'Historica Publishing'),
(10, 'Kinderherz Bücher'),
(7, 'Klartext Verlag'),
(9, 'Mondschein Verlag'),
(2, 'Nordlicht Press'),
(3, 'Südwind Bücher');

--
-- Indizes der exportierten Tabellen
--

--
-- Indizes für die Tabelle `adresse`
--
ALTER TABLE `adresse`
  ADD PRIMARY KEY (`adresse_id`);

--
-- Indizes für die Tabelle `adressenzuordnung`
--
ALTER TABLE `adressenzuordnung`
  ADD PRIMARY KEY (`adresse_id`,`user_id`),
  ADD KEY `idx_adressenzuordnung_user` (`user_id`),
  ADD KEY `idx_adressenzuordnung_adresse` (`adresse_id`);

--
-- Indizes für die Tabelle `ausgabe`
--
ALTER TABLE `ausgabe`
  ADD PRIMARY KEY (`ausgabe_id`),
  ADD KEY `idx_ausgabe_buch` (`buch_id`),
  ADD KEY `idx_ausgabe_verlag` (`verlag_id`);

--
-- Indizes für die Tabelle `ausleihvorgang`
--
ALTER TABLE `ausleihvorgang`
  ADD PRIMARY KEY (`ausleih_id`),
  ADD KEY `idx_ausleih_verleiher` (`verleiher`),
  ADD KEY `idx_ausleih_ausleiher` (`ausleiher`),
  ADD KEY `idx_ausleih_exemplar` (`exemplar_id`),
  ADD KEY `idx_ausleih_status` (`status`),
  ADD KEY `idx_ausleih_datum` (`datum_ausleihe`),
  ADD KEY `idx_ausleih_frist` (`frist`),
  ADD KEY `idx_ausleih_exemplar_status` (`exemplar_id`,`status`);

--
-- Indizes für die Tabelle `ausleihvorgang_archiv`
--
ALTER TABLE `ausleihvorgang_archiv`
  ADD PRIMARY KEY (`ausleih_id`),
  ADD KEY `idx_ausleih_verleiher` (`verleiher`),
  ADD KEY `idx_ausleih_ausleiher` (`ausleiher`),
  ADD KEY `idx_ausleih_exemplar` (`exemplar_id`),
  ADD KEY `idx_ausleih_status` (`status`),
  ADD KEY `idx_ausleih_datum` (`datum_ausleihe`),
  ADD KEY `idx_ausleih_frist` (`frist`),
  ADD KEY `idx_ausleih_exemplar_status` (`exemplar_id`,`status`);

--
-- Indizes für die Tabelle `autor`
--
ALTER TABLE `autor`
  ADD PRIMARY KEY (`autor_id`);

--
-- Indizes für die Tabelle `autorenzuordnung`
--
ALTER TABLE `autorenzuordnung`
  ADD PRIMARY KEY (`autor_id`,`buch_id`),
  ADD KEY `idx_autorenzuordnung_autor` (`autor_id`),
  ADD KEY `idx_autorenzuordnung_buch` (`buch_id`);

--
-- Indizes für die Tabelle `bewertung`
--
ALTER TABLE `bewertung`
  ADD PRIMARY KEY (`bewertung_id`),
  ADD KEY `idx_bewertung_user` (`user_id`),
  ADD KEY `idx_bewertung_buch` (`buch_id`);

--
-- Indizes für die Tabelle `buch`
--
ALTER TABLE `buch`
  ADD PRIMARY KEY (`buch_id`),
  ADD KEY `idx_buch_reihe` (`reihe_id`);

--
-- Indizes für die Tabelle `exemplar`
--
ALTER TABLE `exemplar`
  ADD PRIMARY KEY (`exemplar_id`),
  ADD KEY `idx_exemplar_user` (`user_id_besitzer`),
  ADD KEY `idx_exemplar_ausgabe` (`ausgabe_id`),
  ADD KEY `idx_exemplar_adresse` (`adresse_id`);

--
-- Indizes für die Tabelle `externe_transaktion`
--
ALTER TABLE `externe_transaktion`
  ADD PRIMARY KEY (`schadensmeldung_id`,`transaktions_id`),
  ADD KEY `idx_externetransaktion_meldung` (`schadensmeldung_id`);

--
-- Indizes für die Tabelle `genre`
--
ALTER TABLE `genre`
  ADD PRIMARY KEY (`genre_id`),
  ADD UNIQUE KEY `genre_name` (`genre_name`);

--
-- Indizes für die Tabelle `genrezuordnung`
--
ALTER TABLE `genrezuordnung`
  ADD PRIMARY KEY (`genre_id`,`buch_id`),
  ADD KEY `idx_genrezuordnung_genre` (`genre_id`),
  ADD KEY `idx_genrezuordnung_buch` (`buch_id`);

--
-- Indizes für die Tabelle `lesehistorie`
--
ALTER TABLE `lesehistorie`
  ADD PRIMARY KEY (`user_id`,`exemplar_id`),
  ADD KEY `idx_lesehistorie_user` (`user_id`),
  ADD KEY `idx_lesehistorie_exemplar` (`exemplar_id`),
  ADD KEY `idx_lesehistorie_zeit` (`zeitstempel`);

--
-- Indizes für die Tabelle `lesehistorie_archiv`
--
ALTER TABLE `lesehistorie_archiv`
  ADD PRIMARY KEY (`user_id`,`exemplar_id`),
  ADD KEY `idx_lesehistorie_user` (`user_id`),
  ADD KEY `idx_lesehistorie_exemplar` (`exemplar_id`),
  ADD KEY `idx_lesehistorie_zeit` (`zeitstempel`);

--
-- Indizes für die Tabelle `meldungsbeweis`
--
ALTER TABLE `meldungsbeweis`
  ADD PRIMARY KEY (`meldungsbeweis_id`),
  ADD KEY `idx_meldungsbeweis_meldung` (`usermeldung_id`),
  ADD KEY `idx_meldungsbeweis_user` (`eingereicht_von`);

--
-- Indizes für die Tabelle `meldungsbeweis_archiv`
--
ALTER TABLE `meldungsbeweis_archiv`
  ADD PRIMARY KEY (`meldungsbeweis_id`),
  ADD KEY `idx_meldungsbeweis_meldung` (`usermeldung_id`),
  ADD KEY `idx_meldungsbeweis_user` (`eingereicht_von`);

--
-- Indizes für die Tabelle `meldungsgrund`
--
ALTER TABLE `meldungsgrund`
  ADD PRIMARY KEY (`meldungsgrund_id`);

--
-- Indizes für die Tabelle `meldungsgrundzuordnung`
--
ALTER TABLE `meldungsgrundzuordnung`
  ADD PRIMARY KEY (`usermeldung_id`,`meldungsgrund_id`),
  ADD KEY `idx_meldungsgrundzuordnung_meldung` (`usermeldung_id`),
  ADD KEY `idx_meldungsgrundzuordnung_grund` (`meldungsgrund_id`);

--
-- Indizes für die Tabelle `merkliste_buch`
--
ALTER TABLE `merkliste_buch`
  ADD PRIMARY KEY (`user_id`,`buch_id`),
  ADD KEY `idx_merkliste_buch_user` (`user_id`),
  ADD KEY `idx_merkliste_buch_buch` (`buch_id`);

--
-- Indizes für die Tabelle `merkliste_exemplar`
--
ALTER TABLE `merkliste_exemplar`
  ADD PRIMARY KEY (`user_id`,`exemplar_id`),
  ADD KEY `idx_merkliste_exemplar_user` (`user_id`),
  ADD KEY `idx_merkliste_exemplar_exemplar` (`exemplar_id`);

--
-- Indizes für die Tabelle `nachricht`
--
ALTER TABLE `nachricht`
  ADD PRIMARY KEY (`sender`,`empfaenger`,`zeitpunkt_des_sendens`),
  ADD KEY `idx_nachricht_sender` (`sender`),
  ADD KEY `idx_nachricht_empfaenger` (`empfaenger`),
  ADD KEY `idx_nachricht_zeit` (`zeitpunkt_des_sendens`),
  ADD KEY `idx_nachricht_chat` (`sender`,`empfaenger`,`zeitpunkt_des_sendens`);

--
-- Indizes für die Tabelle `nachricht_archiv`
--
ALTER TABLE `nachricht_archiv`
  ADD PRIMARY KEY (`sender`,`empfaenger`,`zeitpunkt_des_sendens`),
  ADD KEY `idx_nachricht_sender` (`sender`),
  ADD KEY `idx_nachricht_empfaenger` (`empfaenger`),
  ADD KEY `idx_nachricht_zeit` (`zeitpunkt_des_sendens`),
  ADD KEY `idx_nachricht_chat` (`sender`,`empfaenger`,`zeitpunkt_des_sendens`);

--
-- Indizes für die Tabelle `nichtverfuegbarkeitszeitraum`
--
ALTER TABLE `nichtverfuegbarkeitszeitraum`
  ADD PRIMARY KEY (`exemplar_id`,`startdatum`,`enddatum`),
  ADD KEY `idx_nfz_start` (`startdatum`),
  ADD KEY `idx_nfz_ende` (`enddatum`),
  ADD KEY `idx_nfz_exemplar_datum` (`exemplar_id`,`startdatum`,`enddatum`);

--
-- Indizes für die Tabelle `praeferenz`
--
ALTER TABLE `praeferenz`
  ADD PRIMARY KEY (`user_id`,`genre_id`),
  ADD KEY `idx_praeferenz_user` (`user_id`),
  ADD KEY `idx_praeferenz_genre` (`genre_id`);

--
-- Indizes für die Tabelle `reihe`
--
ALTER TABLE `reihe`
  ADD PRIMARY KEY (`reihe_id`);

--
-- Indizes für die Tabelle `schadensbeweis`
--
ALTER TABLE `schadensbeweis`
  ADD PRIMARY KEY (`schadensbeweis_id`),
  ADD KEY `idx_schadensbeweis_meldung` (`schadensmeldung_id`),
  ADD KEY `idx_schadensbeweis_user` (`eingereicht_von`);

--
-- Indizes für die Tabelle `schadensbeweis_archiv`
--
ALTER TABLE `schadensbeweis_archiv`
  ADD PRIMARY KEY (`schadensbeweis_id`),
  ADD KEY `idx_schadensbeweis_meldung` (`schadensmeldung_id`),
  ADD KEY `idx_schadensbeweis_user` (`eingereicht_von`);

--
-- Indizes für die Tabelle `schadensmeldung`
--
ALTER TABLE `schadensmeldung`
  ADD PRIMARY KEY (`schadensmeldung_id`),
  ADD KEY `idx_schadensmeldung_verleiher` (`verleiher`),
  ADD KEY `idx_schadensmeldung_ausleiher` (`ausleiher`),
  ADD KEY `idx_schadensmeldung_exemplar` (`exemplar_id`),
  ADD KEY `idx_schadensmeldung_status` (`status`);

--
-- Indizes für die Tabelle `schadensmeldung_archiv`
--
ALTER TABLE `schadensmeldung_archiv`
  ADD PRIMARY KEY (`schadensmeldung_id`),
  ADD KEY `idx_schadensmeldung_verleiher` (`verleiher`),
  ADD KEY `idx_schadensmeldung_ausleiher` (`ausleiher`),
  ADD KEY `idx_schadensmeldung_exemplar` (`exemplar_id`),
  ADD KEY `idx_schadensmeldung_status` (`status`);

--
-- Indizes für die Tabelle `user`
--
ALTER TABLE `user`
  ADD PRIMARY KEY (`user_id`);

--
-- Indizes für die Tabelle `usermeldung`
--
ALTER TABLE `usermeldung`
  ADD PRIMARY KEY (`usermeldung_id`),
  ADD KEY `idx_usermeldung_melder` (`melder`),
  ADD KEY `idx_usermeldung_gemeldeter` (`gemeldeter`),
  ADD KEY `idx_usermeldung_status` (`status`);

--
-- Indizes für die Tabelle `usermeldung_archiv`
--
ALTER TABLE `usermeldung_archiv`
  ADD PRIMARY KEY (`usermeldung_id`),
  ADD KEY `idx_usermeldung_melder` (`melder`),
  ADD KEY `idx_usermeldung_gemeldeter` (`gemeldeter`),
  ADD KEY `idx_usermeldung_status` (`status`);

--
-- Indizes für die Tabelle `verlag`
--
ALTER TABLE `verlag`
  ADD PRIMARY KEY (`verlag_id`),
  ADD UNIQUE KEY `name` (`name`);

--
-- AUTO_INCREMENT für exportierte Tabellen
--

--
-- AUTO_INCREMENT für Tabelle `adresse`
--
ALTER TABLE `adresse`
  MODIFY `adresse_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=12;

--
-- AUTO_INCREMENT für Tabelle `ausgabe`
--
ALTER TABLE `ausgabe`
  MODIFY `ausgabe_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=12;

--
-- AUTO_INCREMENT für Tabelle `ausleihvorgang`
--
ALTER TABLE `ausleihvorgang`
  MODIFY `ausleih_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=32;

--
-- AUTO_INCREMENT für Tabelle `ausleihvorgang_archiv`
--
ALTER TABLE `ausleihvorgang_archiv`
  MODIFY `ausleih_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=11;

--
-- AUTO_INCREMENT für Tabelle `autor`
--
ALTER TABLE `autor`
  MODIFY `autor_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=12;

--
-- AUTO_INCREMENT für Tabelle `bewertung`
--
ALTER TABLE `bewertung`
  MODIFY `bewertung_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=12;

--
-- AUTO_INCREMENT für Tabelle `buch`
--
ALTER TABLE `buch`
  MODIFY `buch_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=13;

--
-- AUTO_INCREMENT für Tabelle `exemplar`
--
ALTER TABLE `exemplar`
  MODIFY `exemplar_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=12;

--
-- AUTO_INCREMENT für Tabelle `genre`
--
ALTER TABLE `genre`
  MODIFY `genre_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=13;

--
-- AUTO_INCREMENT für Tabelle `meldungsbeweis`
--
ALTER TABLE `meldungsbeweis`
  MODIFY `meldungsbeweis_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=12;

--
-- AUTO_INCREMENT für Tabelle `meldungsbeweis_archiv`
--
ALTER TABLE `meldungsbeweis_archiv`
  MODIFY `meldungsbeweis_id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT für Tabelle `meldungsgrund`
--
ALTER TABLE `meldungsgrund`
  MODIFY `meldungsgrund_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=12;

--
-- AUTO_INCREMENT für Tabelle `reihe`
--
ALTER TABLE `reihe`
  MODIFY `reihe_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=23;

--
-- AUTO_INCREMENT für Tabelle `schadensbeweis`
--
ALTER TABLE `schadensbeweis`
  MODIFY `schadensbeweis_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=12;

--
-- AUTO_INCREMENT für Tabelle `schadensbeweis_archiv`
--
ALTER TABLE `schadensbeweis_archiv`
  MODIFY `schadensbeweis_id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT für Tabelle `schadensmeldung`
--
ALTER TABLE `schadensmeldung`
  MODIFY `schadensmeldung_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=12;

--
-- AUTO_INCREMENT für Tabelle `schadensmeldung_archiv`
--
ALTER TABLE `schadensmeldung_archiv`
  MODIFY `schadensmeldung_id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT für Tabelle `user`
--
ALTER TABLE `user`
  MODIFY `user_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=33;

--
-- AUTO_INCREMENT für Tabelle `usermeldung`
--
ALTER TABLE `usermeldung`
  MODIFY `usermeldung_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=12;

--
-- AUTO_INCREMENT für Tabelle `usermeldung_archiv`
--
ALTER TABLE `usermeldung_archiv`
  MODIFY `usermeldung_id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT für Tabelle `verlag`
--
ALTER TABLE `verlag`
  MODIFY `verlag_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=12;

--
-- Constraints der exportierten Tabellen
--

--
-- Constraints der Tabelle `adressenzuordnung`
--
ALTER TABLE `adressenzuordnung`
  ADD CONSTRAINT `adressenzuordnung_ibfk_1` FOREIGN KEY (`adresse_id`) REFERENCES `adresse` (`adresse_id`) ON UPDATE CASCADE,
  ADD CONSTRAINT `adressenzuordnung_ibfk_2` FOREIGN KEY (`user_id`) REFERENCES `user` (`user_id`) ON DELETE CASCADE ON UPDATE CASCADE;

--
-- Constraints der Tabelle `ausgabe`
--
ALTER TABLE `ausgabe`
  ADD CONSTRAINT `ausgabe_ibfk_1` FOREIGN KEY (`buch_id`) REFERENCES `buch` (`buch_id`) ON DELETE CASCADE ON UPDATE CASCADE,
  ADD CONSTRAINT `ausgabe_ibfk_2` FOREIGN KEY (`verlag_id`) REFERENCES `verlag` (`verlag_id`) ON UPDATE CASCADE;

--
-- Constraints der Tabelle `ausleihvorgang`
--
ALTER TABLE `ausleihvorgang`
  ADD CONSTRAINT `ausleihvorgang_ibfk_1` FOREIGN KEY (`verleiher`) REFERENCES `user` (`user_id`) ON DELETE SET NULL ON UPDATE CASCADE,
  ADD CONSTRAINT `ausleihvorgang_ibfk_2` FOREIGN KEY (`ausleiher`) REFERENCES `user` (`user_id`) ON DELETE SET NULL ON UPDATE CASCADE,
  ADD CONSTRAINT `ausleihvorgang_ibfk_3` FOREIGN KEY (`exemplar_id`) REFERENCES `exemplar` (`exemplar_id`) ON DELETE SET NULL ON UPDATE CASCADE;

--
-- Constraints der Tabelle `autorenzuordnung`
--
ALTER TABLE `autorenzuordnung`
  ADD CONSTRAINT `autorenzuordnung_ibfk_1` FOREIGN KEY (`autor_id`) REFERENCES `autor` (`autor_id`) ON UPDATE CASCADE,
  ADD CONSTRAINT `autorenzuordnung_ibfk_2` FOREIGN KEY (`buch_id`) REFERENCES `buch` (`buch_id`) ON DELETE CASCADE ON UPDATE CASCADE;

--
-- Constraints der Tabelle `bewertung`
--
ALTER TABLE `bewertung`
  ADD CONSTRAINT `bewertung_ibfk_1` FOREIGN KEY (`user_id`) REFERENCES `user` (`user_id`) ON DELETE SET NULL ON UPDATE CASCADE,
  ADD CONSTRAINT `bewertung_ibfk_2` FOREIGN KEY (`buch_id`) REFERENCES `buch` (`buch_id`) ON DELETE CASCADE ON UPDATE CASCADE;

--
-- Constraints der Tabelle `buch`
--
ALTER TABLE `buch`
  ADD CONSTRAINT `buch_ibfk_1` FOREIGN KEY (`reihe_id`) REFERENCES `reihe` (`reihe_id`) ON UPDATE CASCADE;

--
-- Constraints der Tabelle `exemplar`
--
ALTER TABLE `exemplar`
  ADD CONSTRAINT `exemplar_ibfk_1` FOREIGN KEY (`ausgabe_id`) REFERENCES `ausgabe` (`ausgabe_id`) ON UPDATE CASCADE,
  ADD CONSTRAINT `exemplar_ibfk_2` FOREIGN KEY (`user_id_besitzer`) REFERENCES `user` (`user_id`) ON DELETE CASCADE ON UPDATE CASCADE,
  ADD CONSTRAINT `exemplar_ibfk_3` FOREIGN KEY (`adresse_id`) REFERENCES `adresse` (`adresse_id`) ON UPDATE CASCADE;

--
-- Constraints der Tabelle `externe_transaktion`
--
ALTER TABLE `externe_transaktion`
  ADD CONSTRAINT `externe_transaktion_ibfk_1` FOREIGN KEY (`schadensmeldung_id`) REFERENCES `schadensmeldung` (`schadensmeldung_id`) ON DELETE CASCADE ON UPDATE CASCADE;

--
-- Constraints der Tabelle `genrezuordnung`
--
ALTER TABLE `genrezuordnung`
  ADD CONSTRAINT `genrezuordnung_ibfk_1` FOREIGN KEY (`genre_id`) REFERENCES `genre` (`genre_id`) ON UPDATE CASCADE,
  ADD CONSTRAINT `genrezuordnung_ibfk_2` FOREIGN KEY (`buch_id`) REFERENCES `buch` (`buch_id`) ON DELETE CASCADE ON UPDATE CASCADE;

--
-- Constraints der Tabelle `lesehistorie`
--
ALTER TABLE `lesehistorie`
  ADD CONSTRAINT `lesehistorie_ibfk_1` FOREIGN KEY (`user_id`) REFERENCES `user` (`user_id`) ON DELETE CASCADE ON UPDATE CASCADE,
  ADD CONSTRAINT `lesehistorie_ibfk_2` FOREIGN KEY (`exemplar_id`) REFERENCES `exemplar` (`exemplar_id`) ON DELETE CASCADE ON UPDATE CASCADE;

--
-- Constraints der Tabelle `meldungsbeweis`
--
ALTER TABLE `meldungsbeweis`
  ADD CONSTRAINT `meldungsbeweis_ibfk_1` FOREIGN KEY (`usermeldung_id`) REFERENCES `usermeldung` (`usermeldung_id`) ON DELETE CASCADE ON UPDATE CASCADE,
  ADD CONSTRAINT `meldungsbeweis_ibfk_2` FOREIGN KEY (`eingereicht_von`) REFERENCES `user` (`user_id`) ON DELETE SET NULL ON UPDATE CASCADE;

--
-- Constraints der Tabelle `meldungsgrundzuordnung`
--
ALTER TABLE `meldungsgrundzuordnung`
  ADD CONSTRAINT `meldungsgrundzuordnung_ibfk_1` FOREIGN KEY (`usermeldung_id`) REFERENCES `usermeldung` (`usermeldung_id`) ON DELETE CASCADE ON UPDATE CASCADE,
  ADD CONSTRAINT `meldungsgrundzuordnung_ibfk_2` FOREIGN KEY (`meldungsgrund_id`) REFERENCES `meldungsgrund` (`meldungsgrund_id`) ON UPDATE CASCADE;

--
-- Constraints der Tabelle `merkliste_buch`
--
ALTER TABLE `merkliste_buch`
  ADD CONSTRAINT `merkliste_buch_ibfk_1` FOREIGN KEY (`user_id`) REFERENCES `user` (`user_id`) ON DELETE CASCADE ON UPDATE CASCADE,
  ADD CONSTRAINT `merkliste_buch_ibfk_2` FOREIGN KEY (`buch_id`) REFERENCES `buch` (`buch_id`) ON DELETE CASCADE ON UPDATE CASCADE;

--
-- Constraints der Tabelle `merkliste_exemplar`
--
ALTER TABLE `merkliste_exemplar`
  ADD CONSTRAINT `merkliste_exemplar_ibfk_1` FOREIGN KEY (`user_id`) REFERENCES `user` (`user_id`) ON DELETE CASCADE ON UPDATE CASCADE,
  ADD CONSTRAINT `merkliste_exemplar_ibfk_2` FOREIGN KEY (`exemplar_id`) REFERENCES `exemplar` (`exemplar_id`) ON DELETE CASCADE ON UPDATE CASCADE;

--
-- Constraints der Tabelle `nachricht`
--
ALTER TABLE `nachricht`
  ADD CONSTRAINT `nachricht_ibfk_1` FOREIGN KEY (`sender`) REFERENCES `user` (`user_id`) ON DELETE CASCADE ON UPDATE CASCADE,
  ADD CONSTRAINT `nachricht_ibfk_2` FOREIGN KEY (`empfaenger`) REFERENCES `user` (`user_id`) ON DELETE CASCADE ON UPDATE CASCADE;

--
-- Constraints der Tabelle `nichtverfuegbarkeitszeitraum`
--
ALTER TABLE `nichtverfuegbarkeitszeitraum`
  ADD CONSTRAINT `nichtverfuegbarkeitszeitraum_ibfk_1` FOREIGN KEY (`exemplar_id`) REFERENCES `exemplar` (`exemplar_id`) ON UPDATE CASCADE;

--
-- Constraints der Tabelle `praeferenz`
--
ALTER TABLE `praeferenz`
  ADD CONSTRAINT `praeferenz_ibfk_1` FOREIGN KEY (`user_id`) REFERENCES `user` (`user_id`) ON DELETE CASCADE ON UPDATE CASCADE,
  ADD CONSTRAINT `praeferenz_ibfk_2` FOREIGN KEY (`genre_id`) REFERENCES `genre` (`genre_id`) ON DELETE CASCADE ON UPDATE CASCADE;

--
-- Constraints der Tabelle `schadensbeweis`
--
ALTER TABLE `schadensbeweis`
  ADD CONSTRAINT `schadensbeweis_ibfk_1` FOREIGN KEY (`schadensmeldung_id`) REFERENCES `schadensmeldung` (`schadensmeldung_id`) ON DELETE CASCADE ON UPDATE CASCADE,
  ADD CONSTRAINT `schadensbeweis_ibfk_2` FOREIGN KEY (`eingereicht_von`) REFERENCES `user` (`user_id`) ON DELETE SET NULL ON UPDATE CASCADE;

--
-- Constraints der Tabelle `schadensmeldung`
--
ALTER TABLE `schadensmeldung`
  ADD CONSTRAINT `schadensmeldung_ibfk_1` FOREIGN KEY (`verleiher`) REFERENCES `user` (`user_id`) ON DELETE SET NULL ON UPDATE CASCADE,
  ADD CONSTRAINT `schadensmeldung_ibfk_2` FOREIGN KEY (`ausleiher`) REFERENCES `user` (`user_id`) ON DELETE SET NULL ON UPDATE CASCADE,
  ADD CONSTRAINT `schadensmeldung_ibfk_3` FOREIGN KEY (`exemplar_id`) REFERENCES `exemplar` (`exemplar_id`) ON DELETE SET NULL ON UPDATE CASCADE;

--
-- Constraints der Tabelle `usermeldung`
--
ALTER TABLE `usermeldung`
  ADD CONSTRAINT `usermeldung_ibfk_1` FOREIGN KEY (`melder`) REFERENCES `user` (`user_id`) ON DELETE SET NULL ON UPDATE CASCADE,
  ADD CONSTRAINT `usermeldung_ibfk_2` FOREIGN KEY (`gemeldeter`) REFERENCES `user` (`user_id`) ON DELETE SET NULL ON UPDATE CASCADE;

DELIMITER $$
--
-- Ereignisse
--
CREATE DEFINER=`root`@`localhost` EVENT `evt_exemplar_verfuegbar_nach_ende` ON SCHEDULE EVERY 1 DAY STARTS '2026-05-11 19:40:57' ON COMPLETION NOT PRESERVE ENABLE DO UPDATE Exemplar e
    SET e.verfuegbar = 1
    WHERE NOT EXISTS (
        SELECT 1
        FROM Nichtverfuegbarkeitszeitraum n
        WHERE n.exemplar_id = e.exemplar_id
          AND CURDATE() BETWEEN n.startdatum AND n.enddatum
    )
    AND EXISTS (
        SELECT 1
        FROM Nichtverfuegbarkeitszeitraum n2
        WHERE n2.exemplar_id = e.exemplar_id
          AND CURDATE() = n2.enddatum + INTERVAL 1 DAY
    )$$

CREATE DEFINER=`root`@`localhost` EVENT `evt_exemplar_verfuegbar_bei_start` ON SCHEDULE EVERY 1 DAY STARTS '2026-05-18 14:39:01' ON COMPLETION NOT PRESERVE ENABLE DO UPDATE Exemplar e
    SET e.verfuegbar = 0
    WHERE EXISTS (
        SELECT 1
        FROM Nichtverfuegbarkeitszeitraum n
        WHERE n.exemplar_id = e.exemplar_id
          AND n.startdatum = CURDATE()
    )$$

CREATE DEFINER=`root`@`localhost` EVENT `evt_archiv_ausleihvorgang` ON SCHEDULE EVERY 1 MONTH STARTS '2026-05-21 14:14:25' ON COMPLETION NOT PRESERVE ENABLE DO BEGIN
    INSERT INTO Ausleihvorgang_archiv
    SELECT *
    FROM Ausleihvorgang
    WHERE datum_ausleihe < DATE_SUB(CURDATE(), INTERVAL 1 YEAR);

    DELETE FROM Ausleihvorgang
    WHERE datum_ausleihe < DATE_SUB(CURDATE(), INTERVAL 1 YEAR);
END$$

CREATE DEFINER=`root`@`localhost` EVENT `evt_archiv_nachricht` ON SCHEDULE EVERY 1 MONTH STARTS '2026-05-21 14:18:18' ON COMPLETION NOT PRESERVE ENABLE DO BEGIN
    INSERT INTO Nachricht_archiv
    SELECT *
    FROM Nachricht
    WHERE zeitpunkt_des_sendens < DATE_SUB(CURDATE(), INTERVAL 1 YEAR);

    DELETE FROM Nachricht
    WHERE zeitpunkt_des_sendens < DATE_SUB(CURDATE(), INTERVAL 1 YEAR);
END$$

CREATE DEFINER=`root`@`localhost` EVENT `evt_archiv_schadensmeldung` ON SCHEDULE EVERY 1 MONTH STARTS '2026-05-21 14:19:04' ON COMPLETION NOT PRESERVE ENABLE DO BEGIN
    INSERT INTO Schadensmeldung_archiv
    SELECT *
    FROM Schadensmeldung
    WHERE zeitpunkt_meldung < DATE_SUB(CURDATE(), INTERVAL 1 YEAR);

    DELETE FROM Schadensmeldung
    WHERE zeitpunkt_meldung < DATE_SUB(CURDATE(), INTERVAL 1 YEAR);
END$$

CREATE DEFINER=`root`@`localhost` EVENT `evt_archiv_schadensbeweis` ON SCHEDULE EVERY 1 MONTH STARTS '2026-05-21 14:19:25' ON COMPLETION NOT PRESERVE ENABLE DO BEGIN
    INSERT INTO Schadensbeweis_archiv
    SELECT *
    FROM Schadensbeweis
    WHERE zeitpunkt_des_einreichens < DATE_SUB(CURDATE(), INTERVAL 1 YEAR);

    DELETE FROM Schadensbeweis
    WHERE zeitpunkt_des_einreichens < DATE_SUB(CURDATE(), INTERVAL 1 YEAR);
END$$

CREATE DEFINER=`root`@`localhost` EVENT `evt_archiv_usermeldung` ON SCHEDULE EVERY 1 MONTH STARTS '2026-05-21 14:20:39' ON COMPLETION NOT PRESERVE ENABLE DO BEGIN
    INSERT INTO Usermeldung_archiv
    SELECT *
    FROM Usermeldung
    WHERE zeitpunkt_meldung < DATE_SUB(CURDATE(), INTERVAL 1 YEAR);

    DELETE FROM Usermeldung
    WHERE zeitpunkt_meldung < DATE_SUB(CURDATE(), INTERVAL 1 YEAR);
END$$

CREATE DEFINER=`root`@`localhost` EVENT `evt_archiv_meldungsbeweis` ON SCHEDULE EVERY 1 MONTH STARTS '2026-05-21 14:21:28' ON COMPLETION NOT PRESERVE ENABLE DO BEGIN
    INSERT INTO Meldungsbeweis_archiv
    SELECT *
    FROM Usermeldung
    WHERE zeitpunkt_des_einreichens < DATE_SUB(CURDATE(), INTERVAL 1 YEAR);

    DELETE FROM Meldungsbeweis
    WHERE zeitpunkt_des_einreichens < DATE_SUB(CURDATE(), INTERVAL 1 YEAR);
END$$

CREATE DEFINER=`root`@`localhost` EVENT `evt_archiv_lesehistorie` ON SCHEDULE EVERY 1 MONTH STARTS '2026-05-21 14:24:38' ON COMPLETION NOT PRESERVE ENABLE DO BEGIN
    INSERT INTO Lesehistorie_archiv
    SELECT *
    FROM Lesehistorie
    WHERE zeitstempel < DATE_SUB(CURDATE(), INTERVAL 5 YEAR);

    DELETE FROM Lesehistorie
    WHERE zeitstempel < DATE_SUB(CURDATE(), INTERVAL 5 YEAR);
END$$

DELIMITER ;
COMMIT;

/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;
