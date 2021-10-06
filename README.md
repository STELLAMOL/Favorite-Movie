package net.codejava;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class DBMain {

	public static void main(String[] args) {
		String jdbcurl = "jdbc:sqlite:/C:\\SQLite\\sqlite-tools-win32-x86-3360000\\InterestedMovies.db";
		try {
			Connection connection = DriverManager.getConnection(jdbcurl);
			String sql = "SELECT * FROM InterestedMovies";
			
			Statement statement = connection.createStatement();
			
			ResultSet result = statement.executeQuery(sql);
			
			while (result.next()) {
				String movie_name = result.getString("movie_name");
				String name_of_lead_actor = result.getString("name_of_lead_actor");
				String actress = result.getString("actress");
				Integer year_of_release = result.getInt("year_of_release");
				String director_name = result.getString("director_name");
				
				System.out.println(movie_name + "|" + name_of_lead_actor + "|" + actress + "|" + year_of_release + "|" + director_name);
			}
			
		} catch (SQLException e) {
			System.out.println("Error connecting to SQLite database");
			e.printStackTrace();
		}
		

	}

}
