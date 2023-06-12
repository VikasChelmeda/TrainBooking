# TrainBooking
package com.example.demo.dao;

import org.springframework.data.repository.CrudRepository;
import org.springframework.stereotype.Repository;

import com.example.demo.entity.TrainBooking;
@Repository
public interface trainBookingdao extends  CrudRepository<TrainBooking, Integer>
{

}
package com.example.demo.entity;

import java.util.Date;

import javax.persistence.Column;
import javax.persistence.Entity;
import javax.persistence.GeneratedValue;
import javax.persistence.GenerationType;
import javax.persistence.Id;

@Entity
public class TrainBooking {

	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	private Integer id;
	private String name;
	@Column(unique = true,name="Emailid")
	private String email;
	private String movileNo;
	private Date date;
	private String sourceStation;
	private String destinationStation;
	public Integer getId() {
		return id;
	}
	public void setId(Integer id) {
		this.id = id;
	}
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public String getEmail() {
		return email;
	}
	public void setEmail(String email) {
		this.email = email;
	}
	public String getMovileNo() {
		return movileNo;
	}
	public void setMovileNo(String movileNo) {
		this.movileNo = movileNo;
	}
	public Date getDate() {
		return date;
	}
	public void setDate(Date date) {
		this.date = date;
	}
	public String getSourceStation() {
		return sourceStation;
	}
	public void setSourceStation(String sourceStation) {
		this.sourceStation = sourceStation;
	}
	public String getDestinationStation() {
		return destinationStation;
	}
	public void setDestinationStation(String destinationStation) {
		this.destinationStation = destinationStation;
	}
	@Override
	public String toString() {
		return "TrainBooking [id=" + id + ", name=" + name + ", email=" + email + ", movileNo=" + movileNo + ", date="
				+ date + ", sourceStation=" + sourceStation + ", destinationStation=" + destinationStation + "]";
	}
	
}
package com.example.demo.service;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

import com.example.demo.dao.trainBookingdao;
import com.example.demo.entity.TrainBooking;
@Service
public class TrainBookingService 
{
	@Autowired
	private trainBookingdao dao;
public void insert (TrainBooking tb) {
TrainBooking tbs=dao.save(tb);


}
}
package com.example.demo;

import java.util.Date;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.CommandLineRunner;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

import com.example.demo.entity.TrainBooking;
import com.example.demo.service.TrainBookingService;

@SpringBootApplication
public class TrainBooking2Application implements CommandLineRunner
{
@Autowired
private TrainBookingService trainBookingService;

	public static void main(String[] args) {
		SpringApplication.run(TrainBooking2Application.class, args);
	}
	@Override
	public void run (String...args) throws Exception {
		TrainBooking trainBooking = new TrainBooking();
		trainBooking.setName("Babji");
		trainBooking.setEmail("babji@gmail.com");
		trainBooking.setMovileNo("987654321");
		trainBooking.setSourceStation("jntu");
		trainBooking.setDestinationStation("amerpet");
		trainBooking.setDate(new Date());
		trainBookingService.insert(trainBooking);
	}
	
	

}
spring.jpa.hibernate.ddl-auto=update
spring.datasource.url=jdbc:mysql://localhost:3306/tese5?
spring.datasource.username=root
spring.datasource.password=12345
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.jpa.show-sql=true
spring.jpa.properties.dialect:org.hibernate.dialect.MySQL8Dialect
