 ![logo_ironhack_blue 7](https://user-images.githubusercontent.com/23629340/40541063-a07a0a8a-601a-11e8-91b5-2f13e4e6b441.png)

# Answers

## Iteration 2

**1. Add the `solid` and `chartjs` libraries as new rows to the `jslibraries` table.**

<!-- Your Query Goes Here -->
CREATE TABLE jslibraries(
    name            VARCHAR(17),
    owner           VARCHAR(17),
    description     VARCHAR(113),
    stars           INTEGER,
    url             VARCHAR(42),
    releases        INTEGER,
    licence         VARCHAR(11),
    used_by         INTEGER,
    contributors    INTEGER,
    main_technology VARCHAR(10),
    type            VARCHAR(18),
    release_date    DATE
);


INSERT INTO jslibraries(name, owner, description, stars, url, releases, licence, used_by, contributors, main_technology, type, release_date)
VALUES
  ('react', 'facebook', 'A declarative, efficient, and flexible JavaScript library for building user interfaces.', 174000,'reactjs.org', 138, 'MIT License', 7400000, 1501, 'javascript', 'SPA library', '2014-08-23'),
  ('vue', 'vuejs', 'A Vue.js is a progressive, incrementally-adoptable JavaScript framework for building UI on the web.', 188000, 'vuejs.org', 252, 'MIT License', NULL, 399, 'javascript', 'SPA library', '2016-05-30'),
  ('styled-components', 'styled-components', 'Visual primitives for the component age. Use the best bits of ES6 and CSS to style your apps without stress.', 34600, 'styled-components.com', 195,'MIT License',731000,288,'typescript','CSS-in-JS Library','2016-06-18'),
  ('ant-design', 'ant-design','VAn enterprise-class UI design language and React UI library.',34600,'ant.design',474,'MIT License',233000,1469,'typescript','Components Library','2012-12-16'),
  ('chakra-ui','chakra-ui', '⚡️ Simple, Modular & Accessible UI Components for your React Applications.', 20300, 'chakra-ui.com', 2073, 'MIT License', 23100, 429, 'typescript', 'Components Library', '2018-08-12'),
  ('victory', 'FormidableLabs', 'A collection of composable React components for building interactive data visualizations.', 9100, 'http://formidable.com/open-source/victory/', 214 ,NULL, 9700, 148, 'javascript', 'Charts Library', '2014-08-08'),
  ('pug', 'pugjs', 'Pug – robust, elegant, feature rich template engine for Node.js.', 20300, 'pugjs.org', 244, 'MIT License', 348000, 253, 'javascript', 'Template engine', '2012-02-07'),
  ('hbs', 'pillarjs', 'Express view engine wrapper for Handlebars.', 1500, 'pugjs.org', 44, 'MIT License', NULL, 25, 'javascript', 'Template engine', '2013-08-25'),
  ('bootstrap', 'twbs', 'The most popular HTML, CSS, and JavaScript framework for developing responsive, mobile first projects on the web.', 153000, 'getbootstrap.com', 72, 'MIT License', 2700000, 1240, 'javascript', 'CSS Framework', '2017-10-25'),
  ('materialize', 'Dogfalo', 'Materialize, a CSS Framework based on Material Design.', 36600, 'materializecss.com', 44, 'MIT License', 77200, 261, 'javascript', 'CSS Framework', '2016-08-20'),
  ('moment', 'moment', 'Parse, validate, manipulate, and display dates in javascript.', 45900, 'momentjs.com', 84, NULL, 2500000, 590, 'javascript', 'Date library', '2012-10-08');

<br>


**2. Get all the fields of the library that was released earliest (first).**

<!-- Your Query Goes Here -->
INSERT INTO jslibraries
(name, owner, description, stars, url, releases, licence, used_by, contributors, main_technology, type, release_date)
VALUES
('solid','solidjs','A declarative, efficient, and flexible JavaScript library for building user interfaces.',10700,'solidjs.com',194,'MIT License',624,73,'typescript','UI Library','2011-08-13'),
('chartjs','chartjs','Simple HTML5 Charts using the canvas tag.',54700,'chartjs.org',85,'MIT License',414000,377,'javascript','Charts Library','2011-11-02');
<br>

**3. Get all the fields of the library that was released most recently (last).**
SELECT *
FROM jslibraries
WHERE release_date = (SELECT MAX(release_date) FROM jslibraries);
<!-- Your Query Goes Here -->

<br>

**4. All the libraries released before 2015.**

<!-- Your Query Goes Here -->
SELECT *
FROM jslibraries
WHERE release_date < DATE '2015-01-01';

<br>

**5. Get the `name` and the `release_date` of the libraries without a licence.**
SELECT name, release_date
FROM jslibraries
WHERE licence IS NULL;
<!-- Your Query Goes Here -->

<br>

**6. Get the `name` and the `stars` from all CSS Framework libraries.**
SELECT name, stars
FROM jslibraries
WHERE type = 'CSS Framework';
<!-- Your Query Goes Here -->

<br>

**7. Get the `name` of the libraries where the main technology is Typescript.**
SELECT name
FROM jslibraries
WHERE LOWER(main_technology) = 'typescript';
<!-- Your Query Goes Here -->

<br>

**8. Get the `name` and the `type` of all the libraries with more than 1000 contributors.**
SELECT name, type
FROM jslibraries
WHERE contributors > 1000;
<!-- Your Query Goes Here -->

<br>

**9. Get the total number of `stars` of all the libraries.**
SELECT SUM(stars) AS total_stars
FROM jslibraries;
<!-- Your Query Goes Here -->

<br>

**10. Get the average number of `contributors` for all the libraries.**
SELECT AVG(contributors) AS avg_contributors
FROM jslibraries;
<!-- Your Query Goes Here -->

<br>

**11. Update the `licence` field of the libriaries without a licence to store `'unknown'` instead of `NULL`.**
UPDATE jslibraries
SET licence = 'unknown'
WHERE licence IS NULL;

<!-- Your Query Goes Here -->

<br>

**12. Update the `used_by` field of the libraries that don't have it specified to store `0` ( i.e., number zero), instead of `NULL`.**
UPDATE jslibraries
SET used_by = 0
WHERE used_by IS NULL;
<!-- Your Query Goes Here -->

<br>

**13. Update all the records to capitalize the string provided in the `main_technology` field.**
UPDATE jslibraries
SET main_technology = INITCAP(main_technology);
<!-- Your Query Goes Here -->

<br>

**14. Delete all the records where `licence` is `'unknown'`.**
DELETE FROM jslibraries
WHERE licence = 'unknown';
<!-- Your Query Goes Here -->

<br>

**15. Delete all the records with 10000 or less `stars`.**
DELETE FROM jslibraries
WHERE stars <= 10000;
<!-- Your Query Goes Here -->

<br>

**16. Delete all the records with less than 100 `releases`.**
DELETE FROM jslibraries
WHERE releases < 100;
<!-- Your Query Goes Here -->

<br>
