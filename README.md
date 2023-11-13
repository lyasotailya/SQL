CREATE TABLE IF NOT EXISTS Genre (
	Genre_id SERIAL PRIMARY KEY,
	Genre_title VARCHAR(40) UNIQUE NOT NULL
);

CREATE TABLE IF NOT EXISTS Executor (
	Executor_id SERIAL PRIMARY KEY,
	Name VARCHAR(40) NOT NULL
);

CREATE TABLE IF NOT EXISTS Album (
	Album_id SERIAL PRIMARY KEY,
	Album_title VARCHAR(40) NOT NULL,
	Release DATE
);

CREATE TABLE IF NOT EXISTS Song (
	Song_id SERIAL PRIMARY KEY,
	Name_of_song VARCHAR(40) NOT NULL,
	Duration INTEGER NOT NULL CHECK (phone_number BETWEEN 0 and 300),
	Album_id INTEGER NOT NULL REFERENCES Album(Album_id)
);

CREATE TABLE IF NOT EXISTS Collection (
	Collection_id SERIAL PRIMARY KEY,
	Name VARCHAR(40) UNIQUE NOT NULL,
	Release DATE
);

CREATE TABLE GenreExecutor (
    GenreExecutor_id SERIAL PRIMARY KEY,
    Executor_id INTEGER NOT NULL REFERENCES Executor(Executor_id), 
    Genre_id INTEGER NOT NULL REFERENCES Genre(Genre_id)
);

CREATE TABLE AlbumExecutor (
    AlbumExecutor_id SERIAL PRIMARY KEY,
    Album_id INTEGER NOT NULL REFERENCES Album(Album_id), 
    Executor_id INTEGER NOT NULL REFERENCES Executor(Executor_id)
);

CREATE TABLE CollectionSong (
    CollectionSong_id SERIAL PRIMARY KEY,
    Collection_id INTEGER NOT NULL REFERENCES Collection(Collection_id), 
	Album_id INTEGER NOT NULL REFERENCES Album(Album_id), 
    Song_id INTEGER NOT NULL REFERENCES Song(Song_id)
);