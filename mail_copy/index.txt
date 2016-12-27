var express = require('express');
var app = express();
var bParser = require('body-parser');
var mongoose = require('mongoose');


Genres = require('./models/genre');


mongoose.connect("mongodb://localhost/bookstore");
var db = mongoose.connection;

//

app.get('/',function(req,res){
	res.send('hello world');
});
app.get('/api/genres',function(req,res){
	Genre.getGenres(function(err,genres){
		if(err){
			throw err;
		}
		res.json(genres);
	});
});
app.listen(3000);